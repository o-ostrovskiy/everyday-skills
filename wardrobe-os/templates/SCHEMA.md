# Item card schema

One markdown file, `wardrobe/ITEMS.md`, holds every item as a card. No database, no app —
you can read it, grep it, and fix it by hand.

The fields are chosen for what the build algorithm in `PLAYBOOK.md` actually reads.
Nothing decorative: every field is consumed somewhere. If you add a field, say which
step reads it, or don't add it.

| field | values | who reads it |
|---|---|---|
| `id` | `W001`… | addressing. Never reused, never renumbered |
| `photo` | file stem, e.g. `IMG_5835` (may be several) | you, when you forget what it is |
| `category` | `outer` · `top` · `bottom` · `dress` · `layer` · `shoes` · `bag` · `scarf` · `hat` · `belt` · `jewelry` · `swim` · `other` | slot assembly |
| `subcategory` | free text ("denim jacket") | humans |
| `colors` | list | color rules |
| `palette_fit` | `in-palette` · `accent` · `warn` · `off-palette` | priority when choosing. Needs a palette in `PROFILE.md`; leave `—` until then |
| `value` | `light` · `mid` · `dark` | lightness matching, M5 |
| `saturation` | `muted` · `clear` · `neutral` | **M1** |
| `pattern` | `solid` · stripe · check · floral… | color rules, stage protocol |
| `fabric` | the actual fibre | weather, **M2**, **M8** |
| `texture_group` | `dry` · `fluid` | **M2** |
| `fit` | `fitted` · `semi-fitted` · `loose` | V1 vetoes, shape rules |
| `rise` | `high` · `mid` · `low` — bottoms only | proportion rules |
| `length` | `crop` · `hip` · `mid-thigh` · `knee` · `midi` · `maxi` | tuck and jacket rules |
| `formality` | 1–5 | matching the occasion |
| `warmth` | 1–5 | matching the weather |
| `season` | list | seasonal filtering |
| `tuckable` | `yes` · `partly` · `no` | tuck rules |
| `register` | `work` · `smart-casual` · `casual` · `evening` · `utility` · `home` | **M8** |
| `veto_flags` | your own tags, e.g. `tight-at-stomach` · `heel-too-high` | **V1** — hard filter |
| `status` | `active` · `forgotten` · `new` · `rehome` · `alter` | audit |
| `love` | `loved` · `fine` · `dislike` · `?` | priority when choosing, audit |
| `condition` | `like-new` · `good` · `worn` · `replace` · `?` | audit, shopping list |
| `source` | brand, model/SKU, color, size, where and when bought, link | **M4** — whether `fabric`, `fit`, `rise` can be trusted |
| `note` | why the item works, or where it argues with a rule — **citing the rule by number** | humans. This is the most valuable field on the card |

## Card format

```
## W001 · Powder denim jacket
photo: IMG_5835 · category: layer · subcategory: denim jacket
colors: powder pink · palette_fit: in-palette · value: light · saturation: muted
pattern: solid · fabric: denim · texture_group: dry · fit: semi-fitted · length: hip
formality: 3 · warmth: 2 · season: spring, autumn · register: casual
veto_flags: — · status: active
love: loved · condition: like-new
source: Brand "Classic Denim Jacket", Blush · size M · bought 2024-06 · <product url>
note: Length passes the jacket rule. Powder pink is in the palette.
      2026-09-09, tried with layers: nothing in the current rotation goes under it.
      Mechanism: the jacket is semi-fitted and the tops worn now are oversized shirts —
      an oversized sleeve will not go through a semi-fitted armhole.
      ✔ Conclusion is not "bad item" but "it needs its own top": close-fitting or
      thin knit, a tee, a long-sleeve. Not with oversized.
```

## `source` — where fabric and fit actually come from

Optional. Fill it in when you find the item in an order email or on the brand's site.

The point is **reliability**. With no `source`, the fields `fabric`, `fit`, `rise` and
`length` are **a guess from a photograph**, and the guess can be badly wrong — a "mid rise"
that is high, a "semi-fitted" that the maker calls slim, a wrap dress whose wrap is sewn
shut. See **M4** in `RULINGS.md`. With a `source`, the numbers came off the product page
and can be trusted.

Put the product URL in `source` so any claim can be re-checked later.

## `status` values

- `active` — in rotation.
- `forgotten` — owned, not worn. The audit's job is to find it a use or let it go.
- `new` — bought, never worn, tag still on. Gets priority in the daily pick.
- `rehome` — sell, give away, store. **Never suggested in an outfit.**
- `alter` — needs tailoring or repair. Not suggested until fixed.

## `love` and `condition` — why they are separate fields

These are the two things a photograph cannot tell you, and while they are empty, an item
you will never wear ranks alongside a favourite.

- **`love`** is attitude. `loved` rises on a tie; `dislike` is **never suggested**, even
  when every rule says it fits. This is not the same as `status`: an item can be loved and
  unworn (it is waiting for shoes), or unloved and worn constantly (it is the only clean one).
- **`condition`** is state. `replace` is the only honest reason for a line in the
  shopping list that is not a gap.

Filling these two fields across the whole closet is the single highest-value hour you can
spend on this system. `/wardrobe-add triage` walks you through it.

## Conventions that keep the file usable

- ⛔ One item, one card — even if it is on three photographs. Several `photo` values,
  one `id`.
- ⛔ Never renumber. `id`s are referenced from outfits, logs and capsules.
- Unknown value → `?` or `—`. ⛔ Never invent one; write the open question down instead.
- An item in two categories (a shirt worn as a layer) → the category you reach for most,
  and say the other use in `note`.
