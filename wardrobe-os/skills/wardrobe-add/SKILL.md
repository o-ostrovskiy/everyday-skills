---
name: wardrobe-add
description: Adds new items to the wardrobe catalog from photographs, and runs triage over existing items to capture how the owner feels about them and what condition they are in. Use when someone says "/wardrobe-add", "add this item", "I photographed my shoes", "new photos in the folder", "I bought", "add to my wardrobe", or "/wardrobe-add triage".
---

# Add items

Input: `$ARGUMENTS` — a path to photos, `triage`, or nothing (then look for new files
in `photos/`).

**Wardrobe folder:** `~/wardrobe` unless the owner moved it.

## Steps

1. **Find what is unprocessed.** Compare the files in `photos/` against the `photo:`
   values already in `wardrobe/ITEMS.md`. Everything already carded → say there is
   nothing new, and stop.

2. **Convert if needed** (⛔ never touch the originals). On macOS, HEIC → JPEG:
   ```
   sips -Z 1200 -s format jpeg -s formatOptions 70 photos/original/X.HEIC --out photos/full/X.jpg
   ```
   Any resizer works. If the files are already viewable JPEG or PNG, skip this.

3. **Read `wardrobe/SCHEMA.md`, `PROFILE.md`, `RULINGS.md`** (canary
   `wardrobe-rulings-v1`) **and `wardrobe/COVERAGE.md`.**

4. **Look at each photo** and write a card per the schema. `id` is the next free number.
   One item on two frames → **one** card with two `photo` values, not two entries.

5. **In `note`, write why the item works or where it argues with a rule** — citing the
   rule by number. That sentence is the whole value of the card; the fields are just
   filters.
   ⛔ What the photo cannot show — fibre content, how it reads at the face, how it fits,
   heel height, sole, whether a sash is sewn down — **do not invent** (M4). Write the
   question into `OPEN-QUESTIONS.md` and leave the field `?`.

6. **Check for a `source`.** Ask once whether the item can be found in an order email or
   on the brand's site. If it can, take `fabric`, `fit`, `rise`, `length` from there and
   put the URL in `source` — manufacturer data overrides a guess from a photo (M4), and
   this one step corrects more cards than anything else.

7. **Update `wardrobe/COVERAGE.md`.** For every category just added to, ask directly:
   **"is that everything you own in this category, or is there more?"**
   - "that's all" → state `complete`, today's date;
   - "there's more, not photographed" → `partial`, and write what is missing into the
     "what to ask" column.
   ⛔ Do not set `complete` silently just because photos arrived. The difference between
   "I shot everything" and "I shot what was lying out" is the difference between
   "buy a belt" and "check whether you own a belt".

8. **Say what changed in the arithmetic.** A category reaching `complete` → say which
   rules now run on full information and which shopping-list lines that closes or opens.
   A new item with the tag still on → `status: new`, and it gets priority tomorrow.

## `triage` mode — the two fields a photo cannot give you

Run when the owner says `/wardrobe-add triage`, "I've marked everything up", or after the
catalog is first built. Steps 1–2 are skipped.

This is the highest-value hour in the whole system. Until `love` and `condition` are
filled, an item the owner will never wear ranks alongside a favourite.

1. **Walk the catalog in batches of about ten**, oldest `?` first. For each item ask for
   two things — how they feel about it (`loved` / `fine` / `dislike`) and what shape it is
   in (`like-new` / `good` / `worn` / `replace`) — plus anything they want to say in words.
   Let them answer in free form and in any order. ⛔ Do not make them do the whole closet
   in one sitting; save after every batch and tell them where they stopped.

2. **Write it into the cards:**
   - `love: dislike` → `status: rehome`, and the reason, in their words, into `note`;
   - `condition: replace` → `status: rehome`; `worn` → a note, not a verdict (M9);
   - a comment about a specific discomfort ("pulls at the stomach") → a `veto_flags` tag,
     because that is a level-1 veto;
   - "sits like a sack" → into `note`, **not** into `rehome` (M9). Too big and beloved is
     a different case from too big and dead;
   - ⛔ **their words are the most valuable thing here.** Do not paraphrase them into
     neutral language and do not drop them — carry the wording into `note`.

3. **Look for a rule, not just a fact.** If the same thing comes up across several items
   — "hot again", "sack again", "I never reach for this colour" — that is a candidate for
   `RULINGS.md`, **level 1**, as an owner's own finding. Say so out loud and propose the
   rule in one line. ⛔ Do not add it yourself; it is theirs to confirm.

4. **Report briefly:** how many triaged, how many went to `rehome`, what is new, which
   rules you want to propose. ⛔ No item-by-item recap.

## Hard rules

- ⛔ Never delete or rename anything in the originals folder.
- ⛔ Zero items in a category is **not** "they own none". It is "nobody asked".
  This is the single most expensive mistake this system can make: it ends in money spent
  on something already in the drawer.
- ⛔ Never renumber existing `id`s. They are referenced from logs, outfits and capsules.
- An item that is in two categories gets one card, in the category it is reached for most,
  with the other use named in `note`.
