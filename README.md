# Everyday Skills

A collection of practical automations for daily life, built with [Claude](https://claude.ai) (Cowork mode) and connected tools like Notion and TickTick.

Each skill is self-contained — pick what you need and ignore the rest.

## Skills

| Skill | What it does |
|-------|-------------|
| [grocery-automation](./grocery-automation/) | Add groceries during the week → auto-sync to your store's cart on Friday → clear list after shopping |

## How these work

Skills are prompt files that Claude follows when triggered. Scheduled tasks run automatically on a cron schedule. Everything connects via MCP integrations (Notion, TickTick, browser).

**Requirements:**
- [Claude](https://claude.ai) with Cowork mode (for skills + scheduled tasks)
- Notion account (shared database for the whole family)
- TickTick (optional, for task-based triggers)

## Contributing

Have an everyday automation that saves you time? Open a PR — same structure, one folder per skill.
