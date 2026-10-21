---
name: wardrobe-audit
description: Audits the wardrobe — what is missing and in what order to buy it, and above all what to do with the items lying unused. Gives every forgotten scarf and sweater either two or three working outfits or an honest verdict to let it go. Use when someone says "/wardrobe-audit", "what should I buy", "go through my closet", "what do I do with these scarves", "find a use for this", "wardrobe gaps".
---

# Audit

Input: `$ARGUMENTS` — `gaps` (gaps only), `forgotten` (unused items only), or empty (both).

**Wardrobe folder:** `~/wardrobe` unless the owner moved it.

1. **Read:** `RULINGS.md` (canary `wardrobe-rulings-v1`), `PROFILE.md`,
   `wardrobe/ITEMS.md`, `wardrobe/COVERAGE.md`, `logs/WEAR-LOG.md`, `outfits/OUTFITS.md`,
   `PLAYBOOK.md`.

## A. Find a use for what is lying unused

Do this part **first**. It costs nothing and it is where the value is: a closet usually
has more unused capacity than it has gaps.

2. Take everything with `status: forgotten` and `status: new`.
   ⛔ **Check the log.** An item worn in the last 60 days cannot be forgotten, whatever
   the card says: fix `status` to `active` and say you did. The card records intent, the
   log records fact — **fact wins**.
   An item away for repair, lent out, or stored for the season → ask before calling it
   forgotten.

3. **For each item, run `PLAYBOOK.md` honestly** and try to build 2–3 outfits from what
   is actually in the catalog. ⛔ Not hypothetical outfits with items that would need buying.

4. **A verdict per item:**
   - **Works** — show the outfits, set `status: active`.
   - **Works with a caveat** — name the technique (scarf border-out rather than at the
     neck; as a belt; on the bag) and show one outfit using it.
   - **Does not work** — say plainly why, cite the rule, set `status: rehome`.
     ⛔ Do not invent a strained scenario to rescue an item. An honest verdict is more
     useful, and the owner can already tell the difference.
   - **Needs one thing** — it works, but only once a specific item exists. That is the
     strongest kind of shopping-list line: say how many outfits it unlocks.

## B. Find what is missing

5. **Gaps by occasion and temperature coverage**, not against an abstract idea of a
   "capsule wardrobe". The question is: for which occasion, at which temperature, is there
   nothing to wear? That produces three real lines instead of thirty aspirational ones.

6. **Prioritise.** First whatever unlocks the most outfits from what is already owned.
   Expense and fashion are not arguments. Say the number: "wide taupe trousers → +9 outfits."

7. **Check `wardrobe/COVERAGE.md` before every single line.**
   - category `complete` → a real gap, write it into `SHOPPING-LIST.md`:
     item · why · what it unlocks · priority;
   - category `partial` or `unknown` → ⛔ **not a gap.** Write a question with a ❓ and ask
     for a photo. You can always buy later; returning is harder.

8. **If the system is new**, say what the audit could not see: with few log entries there
   is no basis for judging what gets worn, only what was intended. Say it in one line and
   do not pad the output to look thorough.

## Hard rules

- ⛔ No shop links and no specific products unless asked. The output is gaps and
  priorities; shopping is a separate decision and a separate mood.
- ⛔ Never call something a gap just because it is absent from the catalog.
  See `wardrobe/COVERAGE.md`. Absent from the catalog ≠ absent from the closet.
- ⛔ Do not decide for the owner that an item is unnecessary because it breaks a level-2
  rule. Level 2 is a preference. `rehome` is for level-1 breaches, for fit, and for their
  own "I don't wear this".
- "Worn-looking" does not mean "replace" (M9). Loved items stay in rotation until the
  owner says otherwise.
- Say how many outfits a line unlocks, or do not write the line.
