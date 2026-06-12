---
name: friday-cart-sync
description: Every Friday — move weekly shopping needs from Notion into your grocery store's online cart
schedule: "0 9 * * 5"  # Every Friday at 9am local time
---

## Configuration

Update these values before activating:

- **NOTION_DATABASE_ID**: Data source ID of your "Weekly Shopping Needs" Notion database
- **STORE_LIST_URL**: URL of your shopping list on the store's website
- **STORE_NAME**: Name of your grocery store (e.g. "Wegmans", "Whole Foods")
- **STORE_LOCATION**: Your store's address (helps Claude pick the right location if prompted)

---

## Instructions

It's Friday shopping prep! Here's what to do:

1. **Read the weekly needs from Notion:**
   - Use `notion-fetch` with the `NOTION_DATABASE_ID`
   - Extract all item names from the "Item" title property of each page
   - If there are no items, stop and send: "No new items to add this week."

2. **Add each item to the store's online list** using Claude in Chrome:
   - Navigate to `STORE_LIST_URL` (you are already logged in)
   - Scroll to the "Got it" / checked-off section at the bottom of the list
   - For each item from Notion, find it in the "Got it" section and **uncheck it** (this moves it back to the active shopping list)
   - If an item is NOT in "Got it", search for it on the store's website and add it to the list normally

3. **Send a summary:** "Added X items to your `STORE_NAME` list: [item names]. Ready for shopping! 🛒"

**Note:** Do not clear the Notion database — that happens Monday after shopping is confirmed done.
