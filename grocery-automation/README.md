# Grocery Automation

Hands-free weekly grocery management using Claude, Notion, and your grocery store's website.

## What it does

- **During the week**: Say "we need milk" → Claude adds it to your shared Notion list (works from any device, any family member)
- **Friday**: Claude automatically unchecks items from your store's "already bought" list, moving them back to active
- **After shopping**: Check off "Shopping done" in TickTick → Monday morning Claude clears the Notion list for the new week

## Setup

See the [full setup guide](./setup/README.md).

**Quick overview:**
1. Create a Notion database (schema below)
2. Add your store's master product list as a Notion page
3. Install the Claude skill
4. Set up the two scheduled tasks
5. Create a recurring Sunday task in TickTick

## Notion database schema

**Database name:** Weekly Shopping Needs

| Property | Type | Notes |
|----------|------|-------|
| Item | Title | Exact product name |
| Added By | Text | Who added it |
| Date Added | Date | When it was added |

## Files

```
grocery-automation/
├── skills/
│   └── add-to-shopping-needs/
│       └── SKILL.md          ← Install in Claude Cowork
├── scheduled-tasks/
│   ├── friday-cart-sync/
│   │   └── SKILL.md          ← Runs every Friday at 9am
│   └── weekly-cleanup/
│       └── SKILL.md          ← Runs every Monday at 8am
├── setup/
│   └── README.md             ← Step-by-step setup guide
└── chatgpt-prompt.md         ← For family members using ChatGPT
```

## Adapting to your store

The Friday task uses Claude in Chrome to interact with your grocery store's website. Update these values in `scheduled-tasks/friday-cart-sync/SKILL.md`:

- `STORE_LIST_URL` — URL of your shopping list on the store's website
- `STORE_NAME` — name of your store
- `STORE_LOCATION` — your store's address (helps Claude find the right location)

## Family sharing

- Share the Notion database with family members (Notion → Share → invite by email)
- Family members with Claude can install the skill and add items from any device
- Family members with ChatGPT can use the prompt in `chatgpt-prompt.md`
- Anyone can add items directly in the Notion app
