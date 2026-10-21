---
name: wardrobe-setup
description: Sets up a personal wardrobe system from scratch — interviews the owner, writes their profile, config, rules and coverage files, then explains how to build the catalog. Use when someone says "/wardrobe-setup", "set up my wardrobe", "I want the wardrobe system", or has installed the wardrobe skills but has no data files yet.
---

# Set up the wardrobe

Input: `$ARGUMENTS` — nothing, or the folder to use.

**Wardrobe folder:** `~/wardrobe` unless the owner names another. All paths below are
relative to it.

**Templates** come from the `wardrobe-os/templates/` folder of the repo this skill shipped
in. The setup guide copies them into the wardrobe folder before you run. If they are not
there, ⛔ do not reconstruct them from memory — ask the owner for the path to the repo
folder, or tell them to run step 2 of `wardrobe-os/setup/README.md` first. `PLAYBOOK.md`
and `SCHEMA.md` especially: those two carry the whole build algorithm and data format, and
an approximation of them silently breaks every other skill.

## What you are building

Six files. Together they are the whole system — the skills are just readers.

```
PROFILE.md            who is being dressed
CONFIG.md             city, weather, occasions, stage protocol
RULINGS.md            the rules. Two levels. Read first by every skill
PLAYBOOK.md           the build algorithm (copied as-is, not interviewed)
wardrobe/SCHEMA.md    the item card schema (copied as-is)
wardrobe/COVERAGE.md  how complete the catalog is
wardrobe/ITEMS.md     the catalog — starts empty, filled by /wardrobe-add
logs/WEAR-LOG.md      what was actually worn — starts empty
outfits/OUTFITS.md    outfits that have been tried — starts empty
```

## How to run the interview

⛔ **One question at a time.** Not a numbered list of eight questions — one question,
wait for the answer, then the next. Someone setting up a wardrobe is usually standing in
front of a closet on their phone, and a wall of questions gets one answer out of eight.

- Repeat back what you understood before moving on, in one short clause.
- "I don't know" and "skip" are complete answers. Write `?` and move on.
- ⛔ Never fill a field with a plausible guess. A blank field makes the system cautious;
  an invented one makes it confident and wrong.

## Steps

1. **Check the skeleton.** All six templates present, `wardrobe/ITEMS.md`,
   `logs/WEAR-LOG.md` and `outfits/OUTFITS.md` created (empty is correct). Anything
   missing → copy it in before interviewing. ⛔ Do not edit `PLAYBOOK.md` or `SCHEMA.md`:
   they are the algorithm and the data format, not personal.

2. **Interview, in this order.** The order matters: the vetoes are the part that cannot
   be guessed, so they come before anything optional.

   **a. The week.** "Describe a normal week — where are you, and around whom?"
   This sets the `formality` numbers in `CONFIG.md`, and those numbers drive every outfit.
   A `work` day at a law firm and a `work` day writing code at home are not the same code.

   **b. The place.** City. Look up the coordinates yourself; do not ask for them.
   Then fill the seasonal table from the real climate of that city.
   ⚠️ If the owner describes the climate in a way that contradicts the actual place
   ("warm all year" for a four-season city), write the real climate and say, in one line,
   that you did and why.

   **c. The vetoes — the most important question.** Ask it like this:
   > "What do you never wear, however good it looks? And what happened the last time
   > you tried?"
   Then dig once per answer: a veto is only useful if it names a **property**, not an
   item. "Not that grey sweater" → "what about it? tight at the stomach, or itchy, or
   the colour?" Write the property into `V1` with the reason beside it.
   Keep going until they run out. Four or five is a good first set. Zero is a signal they
   have not thought about it yet — say so, and tell them `V1` will fill up from the wear log.

   **d. Do you have a professional analysis?** A stylist's report, a colour draping, a
   body-shape consult.
   - **Yes** → ask them to paste or point at it. Transcribe its conclusions into
     **level 2** of `RULINGS.md`, one numbered rule at a time, each citing the source and
     page. ⛔ Do not copy the document itself into the repo or anywhere public — it is
     someone else's work. Cite it, keep it local.
   - **No** → leave level 2 empty and say the honest thing: level 2 will grow out of the
     wear log over about a month, and until then the system runs on their vetoes plus the
     mechanics, which is already more than a generic chatbot has.
   ⛔ **Do not offer to determine their colour season or figure type from photographs.**
   It cannot be done reliably, and M6 and M7 in `RULINGS.md` exist precisely because
   photographs lie about colour and about silhouette. Say that plainly if asked.

   **e. Palette.** Only if they have one. Otherwise leave it blank and set `palette_fit`
   to `—` on every item card. An invented palette is worse than no palette.

   **f. The default shape decision.** Explain the three options from playbook step 2 in
   one sentence each, and ask which is their usual. It is a default, not a commitment.

3. **Set the coverage table.** Walk the categories and ask for each: "is what you are
   about to photograph everything you own here, or just what is to hand?"
   Set `unknown` for anything not discussed. ⛔ Do not set `complete` because photos exist.
   Explain once why this file exists: an empty category is a question, never a gap, and
   this is what stops the system sending them to buy a belt they already own.

4. **Write the files.** Then show the owner the two that are theirs — `PROFILE.md` and
   the `V1` block of `RULINGS.md` — and ask for corrections. ⛔ Their correction always
   wins; do not explain why you wrote it the way you did, just fix it.

5. **Explain what happens next**, in three lines:
   - photograph the closet, drop the photos in `photos/`, run `/wardrobe-add`;
   - then run `/wardrobe-add triage` and answer two questions per item — `love` and
     `condition`. These are the only two fields a photograph cannot provide, and while
     they are empty an item they will never wear ranks alongside a favourite;
   - then `/wardrobe-today`, and log what they actually wore. The log is the input, not
     the archive.

6. **Say what the system cannot do yet.** Be specific and short: with an empty catalog it
   cannot build an outfit at all; with an empty `love`/`condition` it picks half-blind;
   with an empty level 2 it has no opinion about their figure. All three fix themselves
   with use — but they should hear it now, not discover it.

## Hard rules

- ⛔ Never write a `PROFILE.md` field from a photograph. Not colouring, not figure type,
  not size.
- ⛔ Never put `complete` in the coverage table on your own initiative.
- ⛔ Never paste a purchased guide, stylist report or its page images into the repository.
  Cite it by page in `PROFILE.md` and keep the file local.
- Keep the canary line at the top of `RULINGS.md`. Every skill checks it.
- If the owner already has these files, ⛔ do not overwrite them. Say what exists and
  offer to fill the gaps instead.
