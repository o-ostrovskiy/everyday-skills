---
name: wardrobe-week
description: Lays the wardrobe out across the week — reads the calendar and the forecast, picks an outfit per day, and makes sure nothing repeats two days running. Use when someone says "/wardrobe-week", "what do I wear this week", "plan my week", "lay out the week", or asks for a week of outfits.
---

# The week

Input: `$ARGUMENTS` — the period. Empty → the next 7 days from today.

**Wardrobe folder:** `~/wardrobe` unless the owner moved it.

## Steps

1. **`RULINGS.md`** (canary `wardrobe-rulings-v1`), then `CONFIG.md`.
   For each day settle not only the occasion but the **job** (the table at the end of
   `RULINGS.md`). A week of five `height` days in a row is not a plan, it is a tic.

2. **Calendar.** Use the connector named in `CONFIG.md` for the period.
   No connector → ask for the week in words. ⛔ Never invent an event.
   Map each day to an occasion code from the event title. Unclear → ask, do not guess.

3. **Weather.** Open-Meteo, 7 days, the query in `CONFIG.md`.

4. **`wardrobe/ITEMS.md`**, `wardrobe/COVERAGE.md`, `PLAYBOOK.md`,
   `outfits/OUTFITS.md`, and **`logs/WEAR-LOG.md`** — what was already worn in the 3 days
   *before* the week starts. Without that, Monday repeats Sunday. Read the tags the same
   way `/wardrobe-today` does.

5. **Build day by day**, with two rules that only exist at week scale:
   - ⛔ The same item not two days running. Every other day is fine.
   - Rotate the bottom harder than the top. There are always fewer bottoms, and a
     repeated bottom is what people notice.
   - Laundry reality: do not plan the same item for Monday and Tuesday and call it
     rotation.

6. **Run the `RULINGS.md` checklist per day, separately.** Level 1 broken → rebuild that
   day. Level 2 → leave it and note the departure on that row.

7. **Hand over a table:** day · event · job · weather · outfit · one line of "why".
   A `tested` column: `✓` for outfits marked tried-and-liked, otherwise `untested`.
   Below the table: what to wash and press in advance, and on which day.

## Hard rules

- ⛔ Never invent an event. The calendar is silent → ask.
- Plan the `stage` days first. They carry the most constraints; everything else bends
  around them.
- A day with nothing to wear → say so plainly, on that row. Write it into
  `SHOPPING-LIST.md` **only if** the category is `complete` in `wardrobe/COVERAGE.md`;
  an incomplete category produces a question ("photograph your shoes"), not a purchase.
- ⛔ Never schedule an outfit marked tried-and-rejected.
- ⛔ Do not plan around weather beyond the forecast horizon as if it were known. Past day
  7, say it is climate normals, not a forecast.
