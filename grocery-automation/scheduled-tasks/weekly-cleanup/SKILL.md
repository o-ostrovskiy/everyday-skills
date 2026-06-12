---
name: weekly-cleanup
description: Every Monday — clear the Notion shopping list if weekend shopping is confirmed done
schedule: "0 8 * * 1"  # Every Monday at 8am local time
---

## Configuration

- **NOTION_DATABASE_ID**: Data source ID of your "Weekly Shopping Needs" Notion database
- **TICKTICK_TASK_TITLE**: Title of your TickTick completion task (e.g. "🛒 Shopping done")

---

## Instructions

Monday morning cleanup — check if weekend shopping is done, then clear the list.

1. **Check TickTick for yesterday's (Sunday's) shopping completion:**
   - Use `list_completed_tasks_by_date` for yesterday's date
   - Look for a task with title containing `TICKTICK_TASK_TITLE`
   - If NOT found as completed, stop silently — shopping hasn't been marked done yet.

2. **If shopping IS confirmed done, clear the Notion database:**
   - Search for all pages in the database using `notion-search` with the parent database ID
   - For each page, call `notion-update-page` with `{"archived": true}`
   - Data source ID: `NOTION_DATABASE_ID`

3. **Send a confirmation:** "✅ Shopping list cleared — fresh start for the week!"

**Note:** Only send a message if items were actually cleared. Stay silent if shopping wasn't marked done.

---

## TickTick setup

Create a recurring all-day task in TickTick:
- **Title:** 🛒 Shopping done (or your `TICKTICK_TASK_TITLE`)
- **Repeats:** Every Sunday
- **No specific time** — mark it done whenever you finish shopping
