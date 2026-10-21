# Everyday Skills

A collection of practical automations for daily life, built with [Claude](https://claude.ai) (Cowork mode) and connected tools like Notion and TickTick.

Each skill is self-contained — pick what you need and ignore the rest.

## Skills

| Skill | What it does |
|-------|-------------|
| [grocery-automation](./grocery-automation/) | Add groceries during the week → auto-sync to your store's cart on Friday → clear list after shopping |
| [wardrobe-os](./wardrobe-os/) | Your closet as markdown files → ask what to wear and get an answer from the clothes you own, the weather outside, and your own rules |

## How these work

Skills are prompt files that Claude follows when triggered. Scheduled tasks run automatically on a cron schedule. Everything connects via MCP integrations (Notion, TickTick, browser).

**Requirements** differ per skill — each folder's README states its own. Across the repo:
- [Claude](https://claude.ai) with Cowork mode (for skills + scheduled tasks), or Claude Code
- Notion account — `grocery-automation` (shared database for the whole family)
- TickTick — `grocery-automation`, optional, for task-based triggers
- A local folder and filesystem access — `wardrobe-os` keeps its data in markdown files
  rather than in a connector

## Contributing

Have an everyday automation that saves you time? Open a PR — same structure, one folder per skill.
