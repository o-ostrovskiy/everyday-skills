---
name: wardrobe-today
description: Builds an outfit for today or for a named occasion out of the real catalog, with live weather and the owner's own rules. Use when someone says "/wardrobe-today", "what should I wear", "what do I wear today", "what should I wear to the meeting", "put an outfit together", or names an event they need dressing for. Never invents an item that is not in the catalog.
---

# What to wear

Input: `$ARGUMENTS` — the occasion, the time, the place. Empty → ask in **one** sentence:
what for, and when.

**Wardrobe folder:** `~/wardrobe` unless the owner moved it. All paths are relative to it.
**Read only what the step names.** The catalog can be long; do not pull it all in at once.

## Steps

1. **`RULINGS.md`** — first, always. Canary `wardrobe-rulings-v1`.
   No canary → stop and say the file has been overwritten. ⛔ Do not improvise rules.

2. **`CONFIG.md`** — settle the occasion code (`work` / `stage` / `dinner` / `travel` /
   `casual`). For `stage`, apply the whole stage protocol, not the parts you remember.
   **And name today's job** (the table at the end of `RULINGS.md`): `comfort` ·
   `invisible` · `put-together` · `height` · `dressed-up`. Default `put-together`.
   The occasion does not imply a job → ask in one short sentence.
   ⛔ "Look taller" is not the default goal. It is the `height` job, one of five.

3. **Weather.** Fetch Open-Meteo with the query in `CONFIG.md` (curl or WebFetch).
   No answer → say so plainly and work from the seasonal table in `CONFIG.md`.
   ⛔ Never invent a temperature.

4. **`wardrobe/ITEMS.md`** — the catalog. Filter out `status: rehome`, `status: alter`
   and `love: dislike`.
   **`wardrobe/COVERAGE.md`** — what is actually known about each category.
   **`logs/WEAR-LOG.md`** — the last 3 days, do not repeat them. And read the tags:
   - an item tagged `not me` in the last 30 days — do not offer it without saying why;
   - tagged `was hot` at a similar temperature — drop its `warmth` by 1;
   - tagged `uncomfortable` — it does not go into an all-day outfit.
   **`outfits/OUTFITS.md`** — outfits already tried, with their verdicts.

5. **`PLAYBOOK.md`** — build by steps 0–8. Make the step-2 shape decision **before**
   choosing items and say out loud which of the three you took. On the `comfort` job it
   is legitimate not to decide — also out loud.

6. **Run the checklist** at the end of `RULINGS.md`:
   - level 1 or a mechanic (V·, M·) broken → rebuild;
   - level 2 broken → **do not rebuild**; write one line naming the rule and the reason.

7. **Hand over 2–3 options** in the playbook step-8 format, differing in mood.
   Tag every freshly built outfit `[untested]`. An outfit from `outfits/OUTFITS.md` marked
   tried-and-liked is `[tested ✓]`, with no hedging.
   Assign shoes and bag by `id` from the catalog. What is not in the catalog: describe it
   in words and say **"that is not in the catalog"** — ⛔ never "you don't have one",
   unless `COVERAGE.md` says that category is `complete`.

8. **Offer the one-item swap:** "I can change one piece — say which to keep. Or shorter:
   simpler / dressier / warmer / flat shoes." If they ask, use playbook step 8b: the
   anchor does not move, only the named slot is rebuilt, then the checklist runs over the
   whole outfit again.

9. **Offer to log it.** Write to `logs/WEAR-LOG.md` only if they say yes. Ask not only
   what they wore but **how it went**, using a tag from the log's fixed set. Ask it short,
   once, and drop it if they decline — a system that nags about logging stops being used,
   and then it learns nothing at all.

## Hard rules

- ⛔ Not one item that is not in `wardrobe/ITEMS.md`. Missing something → say so.
  You may add a line to `SHOPPING-LIST.md` **only if** the category is marked `complete`
  in `COVERAGE.md`. Otherwise it is not a gap, it is a question nobody asked — so ask it.
- ⛔ Never soften a level-1 rule or a `V1` veto. Those are the owner's body and their own
  findings. The list grows — read the file, do not rely on what you remember of it.
- ⚠️ Level 2 **may** yield when the job requires it or the owner asks. They want something
  a level-2 rule discourages → say what the risk is, offer the substitution, and if they
  insist, build it as asked and note the departure. It is their closet; level 2 is advice,
  not a veto.
- ⛔ Never offer an outfit already marked tried-and-rejected.
- Items with `status: forgotten` and `status: new` get priority — getting them into
  rotation is the point.
- ⛔ Do not assert fabric, fit, heel height, sole or fastening from a photograph (M4).
  If it decides the outfit and there is no `source`, ask.
