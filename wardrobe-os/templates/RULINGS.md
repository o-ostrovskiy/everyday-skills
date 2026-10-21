# Rules. Canary: `wardrobe-rulings-v1`

If this canary line is missing, the file was overwritten. Stop and say so.

Every skill reads this file **first**.

---

## Two levels. The difference is the whole point

**Level 1 — hard.** Your body, your life, and what you have verified with your own
eyes. Never yields — not for a clever outfit, not for a good fitting.
Violated → the outfit is rebuilt, no discussion.

**Level 2 — preferences.** Conclusions about your figure and your coloring, usually
from a stylist's analysis. Good defaults, but defaults, not laws. A level-2 rule
yields if any one of these is true:

- **(a)** the outfit was actually worn and logged in `logs/WEAR-LOG.md` as liked.
  Experience on a body beats theory from a photo;
- **(b)** today's job requires something else (see the job table below);
- **(c)** you said otherwise.

In all three cases — **say out loud** which rule yielded and why.
Breaking a rule silently is not allowed. Yielding without a reason is also a violation.

**Why this matters.** Collapse the two levels into one list and the system becomes
either a nag that overrules your body, or a yes-man that forgets your vetoes. The
split is what lets it be firm about the first and flexible about the second.

---

# Level 1 — hard

## V1 — Your vetoes. Not up for discussion

> ✍️ **Fill this in during setup.** This is the most important block in the file,
> and nobody can write it for you. Things that are true about your body and your
> life, that no styling argument may override.

Format: the ban, then what it is actually protecting.

```
- ⛔ <nothing tight across the stomach>   — <because the fabric stops and I spend the day pulling it down>
- ⛔ <no heel above 5 cm>                 — <because I am on my feet and I will carry the shoes home>
- ⛔ <no open toe for work>               — <because it is not acceptable in my office>
- ⛔ <no wide brims>                      — <because they overwhelm my face>
```

Rules of thumb for this block:
- Only put here what you have actually experienced. "I read that rectangles shouldn't…"
  belongs in level 2.
- Phrase it as a ban on a **property**, not on an item: "nothing tight across the
  stomach", not "not that grey sweater".
- It grows. Every time an outfit fails on your body for a reason that will repeat,
  that reason belongs here.

## V2 — Fit notes that override the catalog

> ✍️ Add as you discover them. Example: a label says `relaxed` but the item pulls
> on you anyway — once you have worn it, your experience wins.

---

# Mechanics — shipped with the system

These nine are not about your figure or your coloring. They are about how fabric,
color and photographs behave, and about which data can be trusted. They apply to
everyone, which is why they ship filled in. They sit at level 1 because the ones
about data reliability protect every other rule in the file.

Keep them. Delete one only if you have tested it and it is false for you — and
write down what you saw.

## M1 — Match saturation, not just lightness

Two items can match in lightness and still look like strangers if one color is
dusty and the other is clear.

- ✔ Muted with muted. Clear with clear.
- ✔ Clear with a neutral (cream, grey, taupe, denim) — the neutral absorbs and holds it.
- ⛔ Muted next to clear. Reads as two items from different sets.

**How to check:** squint. If one item steps forward and the other recedes,
saturation is not matched.

## M2 — Match texture

Color agreeing is not yet an outfit. Fabrics have to come from one story.

**Two groups:**
- **Dry and matte:** linen, denim, cotton, knit, tweed, corduroy, suiting wool.
- **Smooth and fluid:** silk, satin, crepe, shiny viscose, chiffon.

- ✔ Inside one group — freely.
- ✔ Across groups — fine, but deliberately and one item at a time: a silk top under
  a tweed jacket works because the jacket holds the frame. That is a technique, not an accident.
- ⛔ Casual texture below and something slippery above with no third element — reads
  like the pieces came out of two different closets.

## M3 — A level-1 rule outranks a level-2 rule, always

Level-2 rules routinely collide with level-1 ones. The classic: "tuck your top in"
versus "nothing tight across the stomach". The veto wins.

That does not mean abandoning the technique — it means executing it so the veto holds:
- ✔ **Knit — tuck with slack.** Tuck, then pull back out 3–4 cm so the fabric hangs
  instead of clinging. A belt or tie holds the waist; the stomach is covered by fabric that falls.
- ✔ **Crisp woven (poplin, muslin, shirting cotton) — tucks flat.** It stands away
  from the body on its own.
- ⛔ **Soft knit tucked smooth into a cinched waistband** — the worst case. The tie
  gathers the fabric, the knit stretches above it, and the thing you were hiding is
  on display precisely there, even though every other rule was satisfied.

**How to check.** Look in the mirror **from the side**, not the front. Head-on, a fold
hides; from the side it is immediately visible.

## M4 — Manufacturer data beats a guess from a photo

Fit, rise, fabric and length filled in by looking at a photograph are wrong often,
and wrong in exactly the fields that decide an outfit. If the item has a `source`
(a receipt, an order email, a product page), the data from there overrides the photo.
With no `source`, those fields are an **assumption**, and no advice may rest on an
assumption the owner cannot re-check by hand.

**Never fill in from a photograph:** fabric, fit, rise, length, **heel height, sole
type, fastening type, and whether a detail is sewn down or actually moves.**

⛔ "Looks tied" does not mean it is tied. Before building advice on untying, moving
or re-tying a sash or a bow, touch it or find it at the manufacturer.

**The useful corollary, which also works for shopping.** A knit top labelled `slim` ·
`fitted` · `body-skimming` is a stomach veto **without a fitting** — that is what the
maker intended, it is not a size question. And the reverse: `relaxed` · `easy` ·
`straight` on a bottom is a signal the item will pass.

## M5 — An all-light (or all-dark) outfit reads flat. You need a tonal step

Matching lightness top to bottom is **safe**. Safe is not the same as good. A solid
pale column tends to look flat and dull even when every rule is formally satisfied.

- ✔ **Light top, darker bottom** — the face is lit and there is a step.
- ✔ **Mid top, light bottom.**
- ⛔ **Light on light with no step** — formally correct, nothing to look at.

This does not contradict "no hard contrast at the waist": that bans a **sharp** color
break. A tonal step inside one muted range is not one. One rule cuts off the extreme,
this one cuts off its opposite — no difference at all.

**Check:** squint at the photo. If top and bottom melt into one pale patch and the eye
has nothing to catch, there is no step.

## M6 — Undertone is judged at the face, in daylight — never from a product photo

Catalog shots and flat-lays lie warm: studio light and the floor underneath pull orange
out of something that is a muted rose in the room.

Until the item has been held up to the face in daylight, a verdict about undertone is
a **hypothesis, not a decision**. Phrase it as "from the photo this looks warm, it needs
a look at the face" — never as "this doesn't suit you".

⛔ And separately: **no hard rejection on color for an item that is not on a body.**
The cost of being wrong is asymmetric — talking someone out of a good item is as bad
as approving a bad one.

## M7 — Pose and light change the silhouette more than the cut does

Mirror shots get taken in different poses: torso turned with a hand on the hip, or
standing square with arms down. That changes how fabric falls, where the bodice pulls,
and whether the waist is visible at all. **The difference between two such shots is
not a difference between two garments.**

- ⛔ Never infer a **property of the item** (size, cut, fit, tucked or not) by comparing
  two shots taken in different poses.
- ✔ Ask: "is this one item or two?", "is that tucked?" One short question is cheaper
  than a wrong recommendation to buy.
- ✔ Ask for a crop of the zone if the detail decides it.
- ✔ Compare a pose only with the **same** pose: square with square, turned with turned.

Related to M6. The part they share: **a photograph is good for noticing a question and
no good for closing one.**

## M8 — Register is set by fabric and details, not by the silhouette

Silhouette answers "does it fit". Register answers "where can I go in it". Different
questions, and the second is not settled by rules about cut.

**What sets register:**
- **fabric:** crisp poplin, oxford, suiting wool → work; viscose, jersey, silk, satin,
  chiffon, muslin → soft, evening or at-home;
- **details:** sharp collar, full button placket, cuffs, patch pockets, epaulettes,
  cargo → utility and work; soft neckline, tucks, drape, no fastening → evening.

**The rule:** before assigning an item to an occasion, name its fabric and two or three
details out loud and ask what language they speak. If the fabric is crisp and holds its
shape, that is work — however good the waist is.

⚠️ This is not a demotion. "Work and smart casual" is most people's week.

## M9 — A loose fit is not by itself a flaw

"Sits like a sack" is not grounds for exclusion, alteration or replacement. Read it
together with how the owner feels about the item and what they actually said. An item
can be too big and beloved and worn constantly; another can be too big and dead weight.
Those are different cases, and only the owner can tell them apart.

Likewise "worn-looking" does not by itself mean "time to replace".

---

## Meta-rules

These govern how the system treats its own data. They are not style rules at all.

- **Fact beats intent.** The catalog says what was meant; the wear log says what happened.
  An item worn last week cannot be "forgotten", whatever its card says.
- **Newer beats older.** Body beats fitting, fitting beats a guess from a photo. When two
  records disagree, the later one wins.
- **Not photographed ≠ does not exist.** See `wardrobe/COVERAGE.md`. An empty category
  is a question, never a gap, and never a shopping-list line.

---

# Level 2 — preferences

> ✍️ **This section starts empty, and that is on purpose.**
>
> If you have an analysis from a stylist — figure type, color season, palette — this is
> where it goes, one numbered rule at a time, each with its source. Those conclusions are
> about you; nobody can ship them in a template, and generic ones would be worse than none.
>
> If you have no analysis, leave this empty and let it grow out of your wear log. After a
> month of logging you will have three or four real rules, and they will be yours.
>
> Format, so a skill can cite it:

```
## R1 — <one line, the rule itself>

<two or three lines: what it does and how to execute it>

*Source: <stylist's analysis, p. 34 · my own finding 2026-05-12 · tried and liked>*
```

A rule you found yourself and verified with your eyes belongs in **level 1**, not here —
it is an observation on a live outfit, not theory from a guide.

---

# Today's job

Chosen **before** building, together with the occasion. "Look taller" and "create a
waist" are one of the jobs, not the goal of every day.

| job | what it is for | what gets stronger | what is released |
|---|---|---|---|
| `comfort` | long days, travel, sick days, no audience | V1, fabrics for the weather, layers | fit and proportion rules drop to suggestions |
| `invisible` | you do not want to be looked at | color-matching rules | shape rules — column by default, no waist drama |
| `put-together` | the default. Work, meetings, errands with people | proportion and texture rules | — |
| `height` | you want the longest line you can get | rise, hem, shoe-tone, column rules | — |
| `dressed-up` | dinner, event, photos | waist, texture, fabric register | shoe-tone may argue with the bottom for the sake of the look |

**Default is `put-together`.** If the occasion does not clearly imply a job, ask in one
short sentence. Level 1 never changes, on any job.

> ✍️ Once level 2 has rules in it, fill in the numbers: `comfort → R5, R6, R7 released`.
> Until then the words are enough.

---

## Quick checklist before handing over an outfit

```
[ ] today's job named out loud

    Hard — a violation means rebuild:
[ ] V1  none of my vetoes is broken
[ ] M1  saturation matched: muted with muted, clear with clear
[ ] M2  textures from one group (dry/matte or smooth/fluid)
[ ] M3  no level-2 technique executed in a way that breaks a level-1 veto
[ ] M4  no claim about fabric, fit, rise, heel or fastening that came from a photo
[ ] M5  there is a tonal step — not one flat patch
[ ] M6  no hard rejection on undertone for anything not held to the face
[ ] M8  fabric and details match the occasion, not just the silhouette

    Preferences — may yield, out loud and with a reason:
[ ] every level-2 rule in the file, by number
[ ] every departure named out loud with its reason
```
