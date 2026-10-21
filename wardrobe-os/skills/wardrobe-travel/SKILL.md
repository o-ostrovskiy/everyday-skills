---
name: wardrobe-travel
description: Builds a travel capsule from the real catalog — a set where everything goes with everything — plus a day-by-day plan and a flat packing list. Use when someone says "/wardrobe-travel", "I'm going on a trip", "build me a capsule", "what should I pack for Lisbon", "packing list", "what to pack", or names a trip with dates.
---

# Travel capsule

Input: `$ARGUMENTS` — city, dates, what the trip involves. What is missing, ask for in
**one** question, not one at a time.

**Wardrobe folder:** `~/wardrobe` unless the owner moved it.

## Steps

1. **`RULINGS.md`** (canary `wardrobe-rulings-v1`), `CONFIG.md`, `PLAYBOOK.md`.
   Name the job for the trip as a whole — usually `comfort`, `put-together` for a
   conference. A trip with one evening in it has two jobs, not one; say so.

2. **Weather at the destination**, not at home. Open-Meteo by the destination's
   coordinates. Dates more than 16 days out → there is no forecast: say so plainly and
   work from climate normals. ⛔ Do not present normals as a forecast.

3. **`wardrobe/ITEMS.md`** and `wardrobe/COVERAGE.md`.

4. **Build on the principle that everything goes with everything:**
   - Collapse the capsule to 2–3 `value` levels so any top works with any bottom.
   - One `saturation` story across the set (M1) — a capsule is where a muted/clear clash
     hurts most, because you cannot escape it for a week.
   - 2–3 bottoms, 4–5 tops, 2 layers. One evening upgrade if the trip has a dinner.
   - **Every top must work with every bottom.** One that doesn't comes out of the capsule.
   - ⛔ Check the whole capsule against the owner's level-2 colour rules as a set, not
     pair by pair — a combination that breaks a rule will happen on day four.
   - One pair of shoes you can walk all day in. This is not negotiable and it is not
     the pretty pair.

5. **Day-by-day plan:** day · occasion · weather · what to wear.

6. **A flat packing list** with `id`s, so the suitcase can be packed against it.
   A separate line for what to wash or repair before leaving, and when.

## Hard rules

- Count the combinations out loud: "4 tops × 3 bottoms = 12 outfits from 7 items."
  That number is the entire point of a capsule.
- ⛔ Never pack an item that works with only one other item.
- ⛔ Never pack an item with `status: alter`, or an outfit marked tried-and-rejected.
- Shoes and bags: assign by `id` where `COVERAGE.md` says `complete`. Where it does not,
  describe in words and say **"not in the catalog"** — never "you don't have".
- Mark the capsule `[untested]` unless its outfits are ones already tried and liked.
  A trip is the worst possible place to discover an outfit does not work.
- ⛔ Do not claim fabric behaviour (wrinkles, dries overnight, packs small) for an item
  with no `source` and no logged experience. Say it is a guess, or ask.
