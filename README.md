# Airport transit data — 50 cities, verified 2026

Fares, journey times, modes, and stop counts for **every airport-to-city
transit option across 50 world airports** (171 options), verified in
July 2026 against the transit operators' official fare pages and
timetables. This is the dataset behind
[travelopshq.com's transfer cost index](https://www.travelopshq.com/airport-transfer-costs-2026)
and its 50 [airport transit guides](https://www.travelopshq.com/transit).

## Files

| File | Contents |
|---|---|
| `data/airport-transfer-costs-2026.csv` / `.json` | One row per transit option: airport, destination, option, mode, local fare, currency, USD midpoint, journey time, stop count, source guide URL |
| `data/summary-2026.json` | One row per city: cheapest public option, cheapest door-to-door option, taxi-to-transit multiple |
| `data/fx-rates.json` | The exact FX rates used for USD normalization (USD base, ECB-adjacent daily rates, dated) |
| `route-specs/*.json` | The full structured route specs: per-line stops, per-leg verified stop counts, fares, times, and major-road annotations |

## Methodology

- Every fare traces to an official operator source; sources are linked in
  each city's guide and the process is documented at
  [travelopshq.com/methodology](https://www.travelopshq.com/methodology).
- Fare ranges are normalized as midpoints. Fares are per person, one-way,
  standard adult tickets.
- "Cheapest public" = lowest-fare rail/regional/bus option listed;
  "door-to-door" = lowest-fare taxi/rideshare/car option.
- Stop counts (`nstops`, `legStops`) appear only where verifiable from
  operator station lists or timetables — variable-stop services are
  deliberately left uncounted.

## License & attribution

[CC BY 4.0](LICENSE) — free to use, share, and adapt (including
commercially) **with credit to TravelOpsHQ and a link to
https://www.travelopshq.com**.

Suggested citation: *TravelOpsHQ, "Airport transfer costs in 50 cities"
(2026), travelopshq.com/airport-transfer-costs-2026.*

Found an error? Open an issue here or use the
[contact form](https://www.travelopshq.com/contact) — corrections ship the
same week they're confirmed.
