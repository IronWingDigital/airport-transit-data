# Airport transit data — 50 cities, verified 2026

Fares, journey times, modes, and stop counts for **every airport-to-city
transit option across 50 world airports** (171 options), checked in
July 2026 against the transit operators' official fare pages and
timetables: 168 of 171 verified against official operator sources; 3
flagged as estimates/unconfirmed (see `estimate` below). This is the dataset behind
[travelopshq.com's transfer cost index](https://www.travelopshq.com/airport-transfer-costs-2026)
and its 50 [airport transit guides](https://www.travelopshq.com/transit).

## Files

| File | Contents |
|---|---|
| `data/airport-transfer-costs-2026.csv` / `.json` | One row per transit option: airport, destination, option, mode, local fare, currency, USD midpoint, journey time, stop count, source guide URL |
| `data/summary-2026.json` | One row per city: cheapest public option, cheapest door-to-door option, taxi-to-transit multiple (computed from the unrounded USD values, then rounded to 1 decimal) |
| `data/fx-rates.json` | The exact FX rates used for USD normalization (USD base, one open.er-api.com snapshot dated 09 Jul 2026) |
| `route-specs/*.json` | The full structured route specs: per-line stops, per-leg verified stop counts, fares, times, and major-road annotations |

## Methodology

- Every fare is checked against official operator sources; sources are
  linked in each city's guide and the process is documented at
  [travelopshq.com/methodology](https://www.travelopshq.com/methodology).
  Fares that could not be confirmed officially are flagged; see
  `estimate` below.
- Fare ranges are normalized as midpoints. Fares are per person, one-way,
  standard adult tickets.
- "Cheapest public" = lowest-fare rail/regional/bus option listed;
  "door-to-door" = lowest-fare taxi/rideshare/car option.
- Stop counts (`nstops`, `legStops`) appear only where verifiable from
  operator station lists or timetables — variable-stop services are
  deliberately left uncounted.

### The `estimate` field

A line in `route-specs/*.json` may carry `"estimate": true`. It marks a
fare we could **not** confirm on an official operator source (for example
a distance-based fare with no published band table, or a route missing
from the operator's own pages); the value is our best estimate and the
city's guide explains why. The field is absent (never `false`) on
verified lines. In this release 3 of 171 lines carry it: CAI
"CTA AC bus (356)", IST "M11 Metro + M2" and IST "Yellow Metered Taxi".
The CSV/JSON option rows do not repeat the flag; join on `slug` +
`option` (= the spec line's `label`). Any summary row built on an
estimated line is marked † on the
[study page](https://www.travelopshq.com/airport-transfer-costs-2026)
and never used to lead a headline.

## License & attribution

[CC BY 4.0](LICENSE) — free to use, share, and adapt (including
commercially) **with credit to TravelOpsHQ and a link to
https://www.travelopshq.com**.

Suggested citation: *TravelOpsHQ, "Airport transfer costs in 50 cities"
(2026), travelopshq.com/airport-transfer-costs-2026.*

Found an error? Open an issue here or use the
[contact form](https://www.travelopshq.com/contact) — corrections ship the
same week they're confirmed.
