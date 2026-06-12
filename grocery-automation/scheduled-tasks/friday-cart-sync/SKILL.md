---
name: friday-cart-sync
description: Every Friday — move weekly shopping needs from Notion into your grocery store's online cart
schedule: "0 9 * * 5"  # Every Friday at 9am local time
---

## Configuration

Update these values before activating:

- **NOTION_DATABASE_ID**: Data source ID of your "Weekly Shopping Needs" Notion database
- **STORE_LIST_URL**: Direct URL to your saved shopping list on the store's website
- **STORE_NAME**: Name of your grocery store (e.g. "Wegmans", "Whole Foods")
- **STORE_LOCATION**: Your store's address (helps Claude pick the right location if prompted)

---

## Instructions

It's Friday shopping prep! Read the weekly needs from Notion and uncheck them from the store's "Got it" list.

**Step 1 — Get items from Notion**
- Use `notion-fetch` with the `NOTION_DATABASE_ID`
- Extract all item names from the "Item" title property
- If no items, stop: "No new items this week."

**Step 2 — Go directly to the shopping list (do NOT use the search bar)**
- Navigate to `STORE_LIST_URL` — this is your saved list, already logged in
- Wait for the page to fully load

**Step 3 — Scroll down to the "Got it" section**
- The list has two sections: active items at the top, "Got it" (checked-off) items at the bottom
- Scroll down past all active items until you see the "Got it" divider
- All previously purchased items live here

**Step 4 — Uncheck each Notion item from "Got it"**
- For each item from Notion, find it in the "Got it" section by scrolling
- Click the checkmark next to it — this moves it back to the active list
- Do this for every item on the Notion list

**Step 5 — Only if an item is genuinely not in "Got it" at all**
- As a last resort only: use the store's search bar to find and add it fresh
- Note it in the summary as "added new"

**Step 6 — Archive Notion entries**
- For each page in the Notion database, call `notion-update-page` with `{"archived": true}` at the top level (not inside properties)

**Step 7 — Send summary**
"Moved X items back to your list: [names]. Ready for shopping! 🛒"
