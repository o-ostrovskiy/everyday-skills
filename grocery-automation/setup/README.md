# Setup Guide — Grocery Automation

## Prerequisites

- [Claude](https://claude.ai) with Cowork mode
- Notion account (free tier works)
- TickTick account (free tier works)
- Your grocery store must have an online shopping list feature

---

## Step 1 — Create the Notion structure

1. Open Notion and create a new page: **"🛒 Family Shopping & Meal Prep"**
2. Inside that page, create a new **Database** called **"Weekly Shopping Needs"** with these properties:

   | Property | Type |
   |----------|------|
   | Item | Title |
   | Added By | Text |
   | Date Added | Date |

3. Note the database's **Data Source ID** (visible in the URL when you open the database, or from the Notion MCP after creation)

4. *(Optional but recommended)* Create a new page inside the same parent called **"Master Product List"** and paste your store's usual product list. This lets Claude resolve "milk" → exact brand name. Format as a markdown list grouped by store section.

5. Share the parent page with all family members: **Share → Invite by email → Edit access**

---

## Step 2 — Connect Notion to Claude

In Claude Cowork:
1. Go to **Settings → Integrations**
2. Connect your Notion account
3. Give Claude access to the "🛒 Family Shopping & Meal Prep" page

---

## Step 3 — Install the skill

1. Copy the `skills/add-to-shopping-needs/SKILL.md` file
2. Update the configuration values at the top:
   - `NOTION_DATABASE_ID` → your database's data source ID
   - `NOTION_MASTER_LIST_ID` → your master list page ID (if using one)
   - `ADDED_BY` → your name
3. In Claude Cowork, go to **Settings → Capabilities → Skills** and install the skill

---

## Step 4 — Set up the Friday task

In Claude Cowork, create a new scheduled task:
- **Schedule:** `0 9 * * 5` (every Friday at 9am)
- **Prompt:** Copy from `scheduled-tasks/friday-cart-sync/SKILL.md`, replacing the configuration values

Run it once manually to pre-approve browser and Notion permissions.

---

## Step 5 — Set up the Monday cleanup task

In Claude Cowork, create a new scheduled task:
- **Schedule:** `0 8 * * 1` (every Monday at 8am)
- **Prompt:** Copy from `scheduled-tasks/weekly-cleanup/SKILL.md`, replacing the configuration values

---

## Step 6 — Create the TickTick trigger

In TickTick, create a new task:
- **Title:** 🛒 Shopping done
- **Repeats:** Every Sunday
- **All day:** Yes (no specific time)

Check it off whenever you finish shopping on the weekend.

---

## Step 7 — Family members

- **Using Claude:** Install the skill (Step 3) with their own `ADDED_BY` name
- **Using ChatGPT:** See `chatgpt-prompt.md` for custom instructions
- **No AI:** Open Notion directly and add items to the database manually

---

## Testing

1. Say "add milk to the list" — Claude should confirm with `Added: [product name] ✓` and it should appear in Notion
2. Run the Friday task manually — it should open your store's website and move items to the active list
3. Mark "Shopping done" in TickTick on a Sunday, then run the Monday task manually — the Notion database should clear
