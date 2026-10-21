# Playbook: how an outfit gets built

Read after `RULINGS.md`. The rules say what is not allowed. The playbook says how to work.

The order of the steps is not decoration. Weather before items, shape before items, bottom
before top, checklist before handing anything over. Build in a different order and you will
fall in love with a top and then bend the rules to keep it.

---

## Step 0. Occasion and today's job

**Occasion** — from `CONFIG.md`: `work` · `stage` · `dinner` · `travel` · `casual`.
The occasion sets the `formality` corridor and the limits on shoes.
`stage` additionally turns on the stage protocol (camera, mic, on your feet all day).

**Job** — from the job table at the end of `RULINGS.md`: `comfort` · `invisible` ·
`put-together` · `height` · `dressed-up`. Default is `put-together`.
The job decides which level-2 rules run at full strength and which drop to suggestions.
Name it out loud in the output.

⛔ Do not treat "look taller" as the default goal. It is the `height` job, one of five.

## Step 1. Weather

Open-Meteo by the coordinates in `CONFIG.md`. You need max/min temperature, chance of
precipitation, wind. ⛔ Never invent a temperature — if the call fails, say so plainly and
work from the seasonal table in `CONFIG.md`.

| temperature | item `warmth` | layers |
|---|---|---|
| above +28 °C / 82 °F | 1 | + a light layer for air conditioning indoors |
| +18…+28 °C / 64…82 °F | 1–2 | second layer optional |
| +10…+18 °C / 50…64 °F | 2–3 | second layer required |
| +2…+10 °C / 36…50 °F | 3–4 | second layer + outerwear |
| below +2 °C / 36 °F | 4–5 | outerwear + hat + scarf + gloves |

Rain — no suede, no pale bottoms. Wind — nothing light and floating.

## Step 2. 🔑 The shape decision

**Made here, before any item is chosen.** This is the step that does the most work, and
the one most likely to be skipped.

Every outfit answers the waist question one of three ways. Pick deliberately:

**A. Create a waist** — for `dinner`, `stage`, meetings, anything where you want shape.
Tools, in order of strength:
1. A wrap. A finished solution, nothing to assemble.
2. A tie at the waist — a shirt or a dress with its own sash.
3. A belt over a dress, or on a high rise.
4. A tuck into a high rise — the everyday version.
5. Volume below with a narrow top: a crop top plus a wide leg.

**B. A column** — for maximum height and composure; `work`, `stage`.
One tone or neighbouring tones from top to bottom, vertical never interrupted.
⚠️ Hold it against **M5**: a column still needs a tonal step, or it reads flat.

**C. Don't decide today** — a legitimate third option when the job is `comfort`.
A loose top over a mid-rise bottom is not a ruined outfit; it is an outfit that is not
about your figure. It does flatten both height and waist, and sometimes that is exactly
what the day needs. But it gets chosen **out loud**, not by default.

⛔ On the `height` and `put-together` jobs option C does not exist — the decision is required.

## Step 3. The bottom — first

Not the top. The bottom sets the whole geometry.

1. Filter by weather and occasion.
2. Apply your rise preference, if you have one. Taking a lower rise than your rule wants
   makes tucking the top mandatory rather than optional.
   On the `comfort` job, rise stops being a priority — take what feels good.
3. Remember the bottom's `value` and `saturation`. The top is chosen against them, not
   the other way round.
4. ⛔ Skip anything with `status: rehome` or `status: alter`, and anything with
   `love: dislike`, however well it fits the rules.

## Step 4. The top

1. Filter by weather, occasion, season.
2. `tuckable: yes` gets priority — or `length: crop`, where no tuck is needed.
3. **Match `value` against the bottom:** light+light, dark+dark, or both mid. Different →
   either change the item or tie them together with a third element in the matching tone.
   Then check **M5**: there has to be a step, not one flat patch.
4. **Match `saturation` (M1):** muted with muted, clear with clear, clear with a neutral.
5. Check the face: **M6** — anything warm or dull-greyed near the face is a hypothesis
   until it has been held up to the face in daylight. Do not reject it, flag it.
6. The top's `formality` must not be below what the occasion needs.
7. **Match `texture_group` (M2)** against the bottom.

## Step 5. The second layer

1. Length by your own jacket rule, if you have one.
2. If the goal is a slimmer line: lighter inside, darker outside.
3. A layer can rescue the item underneath — cover a pattern that argues, hide pockets
   you dislike, make a too-casual top wearable at work. Say which problem it is solving.

## Step 6. Shoes and bag

**Look at `wardrobe/COVERAGE.md` first.** It says what is actually known about the
category. State `complete` — assign by `id` from the catalog. `partial` or `unknown` —
you may describe what is needed in words, but you **must** say the catalog is incomplete,
not that the item does not exist.

- Heel height, sole and fastening are **M4** fields: never read them off a photo.
- Shoes you will stand in all day outrank shoes that finish the look. If the occasion is
  `stage`, this is not a trade-off, it is a veto.
- A bag that ends at or above the hip keeps the line; name the specific bag by `id`.

## Step 7. Scarf, hat, jewelry

- Items with `status: forgotten` get priority here. Getting them back into rotation is
  the whole job of this slot.
- A scarf whose pattern argues near the face can be folded border-out, or moved off the
  neck entirely: onto a bag handle, as a belt (which also answers step 2), as a headband.
- Jewelry has to be visible where you dress or it does not get worn. That is a storage
  problem, not a style problem — say it once and move on.

## Step 8. Checklist and output

Run the checklist at the end of `RULINGS.md`. Then, by level:

- **Level 1 or a mechanic (V·, M·)** violated → go back and rebuild. No discussion.
- **Level 2** violated → **do not rebuild**. Write one line saying which rule yielded and
  why: "R6 yielded, the jacket is long — today's job is comfort."
  A departure with no reason is still a violation; rebuild that one.

**Output format:**
```
Job: put-together · occasion: work · 18…22 °C, rain likely

Option 1 — "name"   [untested]
  Bottom: W0xx · name
  Top:    W0xx · name (tuck fully / front only)
  Layer:  W0xx · name
  Shoes:  W0xx · name — or in words, saying the catalog is incomplete
  Bag:    W0xx · name
  Scarf:  W0xx (optional, and how to wear it)

Why it works: one or two sentences, citing a rule by number.
Watch out for: what might go wrong — the thing to check in the mirror.
Departures: R6 — jacket longer than mid-thigh, job is comfort. (or "none")
```

Give **two or three options**, not one, and make them differ in mood: composed / relaxed.

**The confidence tag is mandatory.** A freshly built outfit goes out as `[untested]` —
it was assembled from catalog photos and nobody has seen it on a body. An outfit from
`outfits/OUTFITS.md` marked tried-and-liked goes out as `[tested ✓]` with no hedging.
⛔ An outfit marked tried-and-rejected is never offered again. It was already judged.

## Step 8b. Change one item

People rarely want the whole thing again. Far more often: "keep the trousers, change the top."

**How it works:** everything not named is the **anchor** and does not move. Only the named
slot is rebuilt.

After the swap, run the checklist over the **whole** outfit, not just the new item — a new
top can fall out with the texture of the bottom that stayed.

- The swap breaks level 1 → refuse with the reason, and offer another item for the same slot.
- The swap breaks level 2 → say what slipped, and leave the choice to the owner.

⛔ Never rebuild from scratch when asked to change one item.

| phrase | what it does |
|---|---|
| "keep the trousers, change the top" | anchor is the bottom; only the top is re-decided |
| "simpler" | `formality` −1, second layer off, casual shoes |
| "dressier" | `formality` +1, add a layer or a scarf |
| "flat shoes" | a constraint on the shoe slot only, everything else holds |
| "warmer" / "cooler" | `warmth` ±1, minimum disturbance |
| "less loud" | drop the accent item, replace with a neutral |

End the output with one line offering this: "I can swap one piece — say which one to keep.
Or shorter: simpler / dressier / warmer / flat shoes."

## Step 9. The log

Offer to write a line into `logs/WEAR-LOG.md`:
`date · outfit · occasion · weather · items · how it went · note`

"How it went" uses a fixed tag set, so the tags can be read mechanically:
`comfortable` · `uncomfortable` · `too dressy` · `too plain` · `was hot` · `was cold` ·
`not me` · `item was unavailable`.

The log is not an archive. It is the **input** to the system:
- a positive tag promotes the outfit to tried-and-liked, and it starts going out as `[tested ✓]`;
- `not me` retires the outfit from circulation entirely;
- `was hot` at a given temperature means dropping that item's `warmth` by 1 next time;
- `uncomfortable` means the item does not go into an all-day outfit again;
- the same tag on three different items is a candidate for a **new level-1 rule**. Say so
  out loud and propose the rule.

This loop is the only reason the system gets better instead of just getting bigger.
⛔ Write to the log only if the owner says yes, and ask it as one short question.
