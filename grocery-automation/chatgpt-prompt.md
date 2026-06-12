# ChatGPT Custom Instructions

For family members who use ChatGPT instead of Claude. Save these in **ChatGPT → Settings → Personalization → Custom Instructions**.

---

## "What would you like ChatGPT to know about you?"

> We do weekly grocery shopping at [STORE_NAME]. I share a grocery database in Notion called "Weekly Shopping Needs" (under the page "[YOUR_NOTION_PAGE_NAME]"). My family handles the automation that adds these items to the store's cart every Friday.

---

## "How would you like ChatGPT to respond?"

> Whenever I mention needing groceries — any phrase like "we need X", "add X to the list", "we're out of X", "pick up X", "running low on X" — immediately add it to our shared Notion "Weekly Shopping Needs" database using the Notion connector. The database has three fields: Item (the product name), Added By (put "[YOUR_NAME]"), and Date Added (today's date). Don't just say "noted" — actually write it to Notion. Confirm with one line: `Added: [item name] ✓`

---

## Setup for ChatGPT

1. Connect Notion: **ChatGPT → Settings → Connected apps → Notion**
2. Make sure the Notion page is shared with your email
3. Paste the instructions above into Custom Instructions
