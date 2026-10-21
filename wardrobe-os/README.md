# Wardrobe OS

A personal wardrobe system in plain markdown files, driven by six Claude skills.
Ask it what to wear, and it answers from the clothes you actually own, the weather
outside, and the rules of your own body.

It is **not** an AI stylist. It will not look at your photos and tell you your colour
season. It is the filing system and the discipline that make a styling analysis — a
professional's, or your own, accumulated over a month of paying attention — usable at
7 a.m. in front of a closet.

## What it actually does

```
/wardrobe-setup    interviews you once and writes your profile, config and rules
/wardrobe-add      photos → item cards; `triage` captures what a photo can't see
/wardrobe-today    an outfit for today: occasion, live weather, 2–3 options, with reasons
/wardrobe-week     the week laid out from your calendar, nothing repeated two days running
/wardrobe-travel   a capsule where everything goes with everything, plus a packing list
/wardrobe-audit    what to do with what you never wear, and what is genuinely missing
```

Everything lives in one folder of markdown files you can read, grep and fix by hand.
No app, no account, no subscription, no photo upload to anyone's server.

## The four ideas that make it work

Most wardrobe apps are a database with a mood board on top. These are the parts that
actually change the advice.

**1. Two levels of rules.** Level 1 is your body and what you have verified yourself —
it never yields, and an outfit that breaks it is rebuilt without discussion. Level 2 is
the conclusions about your figure and colouring — good defaults that yield to three
things: an outfit you actually wore and liked, today's job, or you saying otherwise.
Always out loud, always with a reason.

Collapse those into one list and you get either a nag that overrules your body or a
yes-man that forgets your vetoes. The split is the whole product.

**2. "Not photographed" ≠ "does not exist."** Catalog completeness is tracked separately
from catalog contents, per category, in three states. A category that is `partial` or
`unknown` **cannot** produce a shopping-list line — only a question. This is the single
most expensive mistake a wardrobe system makes: it sends you to buy a belt that is in
your drawer, because the belt was on your waist on photo day.

**3. Fact beats intent, and newer beats older.** The item card says what was meant; the
wear log says what happened. An item worn last week is not "forgotten". A fitting beats
a guess from a photo, and your body beats the fitting. When two records disagree, the
later one wins.

**4. Today's job.** Every outfit gets one of five jobs chosen before any item: `comfort`,
`invisible`, `put-together`, `height`, `dressed-up`. It decides which preferences run at
full strength. "Look taller" is one of five jobs, not the default goal of being dressed —
and a system that forgets that will put you in heels on a travel day.

Plus nine mechanics that ship filled in, because they are about fabric, colour and
photographs rather than about you: match saturation as well as lightness, match texture,
manufacturer data beats a guess from a photo, an all-light outfit reads flat, undertone is
judged at the face in daylight, pose and light change the silhouette more than the cut
does, register is set by fabric and details rather than silhouette. They are in
`templates/RULINGS.md` with the reasoning.

## Requirements

- **Claude with filesystem access** — Claude Code, or the Claude desktop app with a
  folder open. Unlike `grocery-automation` in this repo, this one is not connector-based:
  it reads and writes markdown files on your machine.
- **A folder**, by default `~/wardrobe`. Keep it in Dropbox/iCloud if you want it on your
  phone.
- **Photographs of your clothes.** Lying flat is fine, on a hanger is fine; it does not
  have to be pretty, it has to be identifiable.
- **No API key.** Weather comes from Open-Meteo, which is free and unauthenticated.
- **Optional:** a calendar connector, used only by `/wardrobe-week`.

## Install

See the [setup guide](./setup/README.md). The short version: copy the six skills into
your skills folder, run `/wardrobe-setup`, answer the questions, photograph the closet.

First useful answer: about an hour, most of it photography.

## What it cannot do

Stated plainly, because every one of these has already caught someone out.

- **It cannot determine your colour season or figure type from photographs.** Catalog
  shots lie warm, and mirror shots in different poses lie about silhouette. If you have a
  professional analysis, this system will carry it faithfully. If you don't, level 2
  starts empty and grows out of your wear log over about a month.
- **With an empty catalog it cannot build anything.** It will not invent an item to
  complete an outfit; it will tell you what is missing instead.
- **Until you fill in `love` and `condition` it picks half-blind** — an item you will
  never wear ranks alongside a favourite. That is one hour of `triage`, and it is the
  highest-value hour in the system.
- **It cannot tell you whether something fits.** Fit, fabric, rise, heel height and
  whether a sash is sewn down are not readable from a photograph. It will ask, or say it
  is guessing.
- **It does not learn anything you don't tell it.** The wear log is the input. Skip the
  logging and it stays exactly as clever as it was on day one.

## Credit

Extracted from a working system built with Claude over several weeks, where the level-2
rules came from a professional styling analysis and the level-1 rules were earned one
mistake at a time. The analysis itself is not here and should not be — it is personal, and
it belongs to the stylist who wrote it. What is here is the machinery.

Everything in `templates/` is a blank. Nobody else's body, palette or closet is in this
folder.
