# Config

## Place

> ✍️ Your city and coordinates. Weather drives half the decisions in the playbook, so
> this has to be the place you actually get dressed in, not where you are registered.

**<City>** · <latitude> · <longitude> · timezone <Area/City>

| season | months | what it means for clothes |
|---|---|---|
| winter | | |
| spring | | |
| summer | | |
| autumn | | |

> ✍️ Fill the right column with real consequences, not temperatures: "coat, layers,
> closed shoes", "linen and cotton, but air conditioning indoors means carrying a layer".
> The skills read this when the weather API is unreachable.

⚠️ Answer this from the climate, not from how you feel about it. A place with four real
seasons does not become mild because you prefer summer — and a system configured for
year-round warmth will dress you wrong for five months.

## Weather

Open-Meteo, no API key required. Substitute your coordinates:

```
https://api.open-meteo.com/v1/forecast?latitude=<LAT>&longitude=<LON>&daily=temperature_2m_max,temperature_2m_min,precipitation_probability_max,windspeed_10m_max&timezone=<Area/City>&forecast_days=7
```

Fetch with curl or WebFetch. ⛔ If it is unreachable, say so plainly and plan from the
seasonal table above. Never invent a temperature.

For imperial units add `&temperature_unit=fahrenheit&windspeed_unit=mph`.

## Calendar (optional)

> ✍️ If you have a calendar connector, name the tool here. Used by `/wardrobe-week`.
> Without it, the week skill asks you for the week in words — which works fine, it is
> just one more question.

## Occasions

| code | what it is | formality |
|---|---|---|
| `work` | a normal working day — home, co-working, office | 2–3 |
| `stage` | conference, talk, filming, being photographed | 4–5 |
| `dinner` | dinner, a date, meeting people in the evening | 3–4 |
| `travel` | a trip | per day |
| `casual` | day off, errands, a walk | 1–2 |

> ✍️ Adjust the formality numbers to your life. A `work` that is 4–5 in a law firm is
> 1–2 for someone who writes code at home, and every outfit the system builds depends
> on these two numbers being true for you.

### Stage protocol (`stage`)

Requirements a normal day does not have. These are mechanical, not stylistic — keep them.

- Shoes — **you are on your feet all day**, and you will be the last to leave. Your
  comfort veto applies at its strictest here.
- **Lavalier mic** — you need firm fabric at the neckline, or a waistband the transmitter
  can clip to. ⛔ Thin silk with no support, ⛔ a dress with no belt and no pockets.
- **Camera and lights** — ⛔ small busy patterns (they moiré and vibrate on camera),
  ⛔ pure white (blows out), ⛔ pure black (collapses into shadow).
- A plain mid-saturation top from your palette works better than anything else, every time.
- Pockets or a waistband somewhere. You will be handed a mic pack, a clicker, or both.
