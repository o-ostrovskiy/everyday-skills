# Setup

About an hour, most of it photographing clothes. You can stop after step 4 and come back —
the system works, just with less to work from.

## 1. Make the folder

```bash
mkdir -p ~/wardrobe/{wardrobe,photos/full,photos/original,logs,outfits,capsules}
```

Keep it in Dropbox or iCloud Drive if you want to read it on your phone.

If you want it somewhere else, that is fine — every skill names `~/wardrobe` in one line
near the top, and you change it there.

## 2. Copy in the templates

From this folder in the repo, into your wardrobe folder:

```bash
cp templates/{PROFILE.md,CONFIG.md,RULINGS.md,PLAYBOOK.md} ~/wardrobe/
cp templates/{SCHEMA.md,COVERAGE.md} ~/wardrobe/wardrobe/
touch ~/wardrobe/wardrobe/ITEMS.md ~/wardrobe/logs/WEAR-LOG.md ~/wardrobe/outfits/OUTFITS.md
```

`PLAYBOOK.md` and `SCHEMA.md` are the algorithm and the data format — leave them alone.
The other four are yours and get filled in during setup.

## 3. Install the skills

Copy the six folders from `skills/` into your Claude skills directory:

```bash
cp -R skills/* ~/.claude/skills/
```

- **Claude Code** — `~/.claude/skills/` as above, and they are available as
  `/wardrobe-today` and so on.
- **Claude desktop / Cowork** — add them as skills in the UI, one folder each.

Check: ask Claude `/wardrobe-setup` and see whether it starts asking about your week.

## 4. Run `/wardrobe-setup`

It interviews you one question at a time and writes four files. Budget 15 minutes.

What it will ask, so you can think about the hard one in advance:

1. **Your week** — where you are and around whom. This sets the formality numbers, and
   every outfit depends on them being true for you.
2. **Your city** — for weather. It looks up the coordinates itself.
3. **Your vetoes.** The important one:
   > *What do you never wear, however good it looks? And what happened the last time
   > you tried?*

   Answer in terms of **properties**, not items: "nothing tight across the stomach", not
   "not that grey sweater". Four or five is a good start. These become level 1, and
   nothing overrides them.
4. **Whether you have a professional analysis** — a stylist's report, a colour draping.
   If you do, you will paste its conclusions and they become level 2, cited by page.
   If you don't, level 2 stays empty on purpose. See "About level 2" below.
5. **Your palette**, if you have one. If not, leave it blank — an invented palette is
   worse than none.

⛔ It will not guess your colour season from photos, and you should be suspicious of
anything that offers to.

## 5. Photograph the closet

One frame per item. Flat on the bed, or on a hanger against a plain wall. Phone is fine.

- Daylight if you can, but do not wait for it. The system never judges colour from these
  photos anyway (that is rule M6) — the photos are for recognising the item.
- Shoot **everything in a category or none of it.** This matters more than the photo
  quality: the system tracks per category whether the catalog is complete, and only a
  complete category can generate a shopping recommendation.
- Do not forget what you are currently wearing. Everyday jewellery, the belt in your
  jeans, the shoes by the door — these are the things that never make it into the photos
  and then get bought twice.

Drop the files into `~/wardrobe/photos/original/` (or `photos/full/` if they are already
JPEG) and run:

```
/wardrobe-add
```

It writes a card per item and will ask, per category, whether that was everything.
Answer honestly — "there's more I didn't shoot" is a useful answer.

## 6. Triage — the highest-value hour

```
/wardrobe-add triage
```

Two questions per item: do you love it, and what shape is it in. These are the only two
fields a photograph cannot provide, and while they are empty, a dress you will never
wear again ranks alongside your favourite shirt.

Ten items at a time is plenty. It saves after every batch.

Say whatever you want in words as you go — "too short now", "itchy", "I only wear this
on planes". Those sentences end up on the card and are worth more than the fields.

## 7. Use it, and log it

```
/wardrobe-today
```

Then — this is the part that makes it better rather than just bigger — tell it what you
actually wore and how it went. One tag: `comfortable`, `was hot`, `not me`, `too dressy`.

Each entry changes the next answer mechanically: `not me` retires that outfit, `was hot`
drops that item's warmth, the same tag on three items becomes a proposed new rule.

One tap a day is the entire contribution. Skip it and the system stays exactly as clever
as it was on day one.

## About level 2

Level 2 is where conclusions about your figure and colouring live, and it ships **empty**.
That is deliberate, not unfinished.

Generic rules for "a rectangle" or "a soft autumn" applied to the wrong person are worse
than no rules, because the system will state them with confidence and you will believe it.
So there are two honest paths:

**You have an analysis.** Paste it during setup. It becomes numbered level-2 rules, each
citing its source. The system follows them as defaults and tells you when it departs.
⛔ Keep the document itself local — it is the stylist's work, not yours to republish.

**You don't.** Then level 2 grows out of your wear log. After a month of tags you will
have three or four rules that are genuinely yours — "light on light reads flat on me",
"I never wear the stiff collars I own". Until then the system runs on your vetoes plus
the nine mechanics, which is already more than a generic chatbot has: it knows what you
own, what you never wear, and what the weather is doing.

Rules you find yourself go into **level 1**, not level 2 — an observation on a live
outfit outranks theory from a guide.

## Keeping it honest

Three failure modes, with the fix.

**It recommends buying something you own.** The coverage table has a category marked
`complete` that isn't. Fix the row; the shopping line disappears.

**It keeps suggesting an outfit you hate.** You wore it and didn't log it. One tag retires
it permanently.

**It sounds confident about fabric or fit.** Check for a `source` on that card. With no
source, those fields are a guess from a photograph, and rule M4 says the system must tell
you so. If it didn't, the rules file was probably overwritten — check that the canary line
is still at the top of `RULINGS.md`.
