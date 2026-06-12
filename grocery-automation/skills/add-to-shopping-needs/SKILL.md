---
name: add-to-shopping-needs
description: Add grocery items to the weekly shopping needs list. Use this skill whenever someone mentions needing something, running out of something, or wanting to pick something up at the store. Trigger on any phrase like "I need X", "add X to shopping list", "we're out of X", "get X", "pick up X", "can you add X", "running low on X", or any mention of a grocery item that needs to be bought. Also trigger for multiple items at once like "we need eggs and milk". Always use this skill rather than just saying "noted" — actually write it to the Notion database.
---

## Configuration

Before using this skill, set these values:

- **NOTION_DATABASE_ID**: The data source ID of your "Weekly Shopping Needs" Notion database
- **NOTION_MASTER_LIST_ID**: The page ID of your store's master product list in Notion
- **ADDED_BY**: Your name (e.g. "Olga", "husband") — update per person

## Steps when triggered

1. **Look up the item in the Master List** — fetch the master list page from Notion using `notion-fetch` with the `NOTION_MASTER_LIST_ID`. Find the exact product name the family usually buys (e.g. "milk" → "Horizon Organic Milk, 2% Reduced Fat, 0.5 gallon").

2. **Read the current Weekly Shopping Needs database** — fetch the database using `notion-fetch` with the `NOTION_DATABASE_ID` to see what's already listed.

3. **Check for duplicates** — don't add something already in the database (case-insensitive match on the Item title).

4. **Add the item** — call `notion-create-pages` with:
   ```
   parent: {"type": "data_source_id", "data_source_id": "<NOTION_DATABASE_ID>"}
   pages: [{"properties": {"Item": "<resolved product name>", "Added By": "<ADDED_BY>", "Date Added": "<today's date YYYY-MM-DD>"}}]
   ```

5. **Confirm briefly** — one line: `Added: [Product Name] ✓`

## Matching to master list

For every item — no matter how generic — search the master list and use the exact product name. This ensures the Friday automation finds the right item on the store's website.

- If multiple matches exist (e.g. several yogurt varieties), ask which one — or default to the highest-quantity item on the master list.
- If the item is not on the master list at all, write it as the user said it.
