# warehouse

Historical data from genesis up to now of some Solana DeFi protocols : perp funding rates, lending reserves, vault strategies.

## Layout

```
funding-rates/      perp funding rate history
  SOL/
    drift/{v1,v2,v3}/data.{json,csv}
    hyperliquid/data.{json,csv}
    pacifica/data.{json,csv}

lending/            lending protocol reserve history
  kamino/sol/data.{json,csv}

strategies/         vault/strategy performance history
  kamino/
    jitosol/data.{json,csv}
    msol/data.{json,csv}
```

## Conventions

- One dataset per leaf dir. `data.json` canonical, `data.csv` mirror.
- Path = `<domain>/<asset>/<protocol>/<version?>/data.*`.
- Timestamps vary by source (unix sec, unix ms, ISO-8601) — check per-file.
- Append-only snapshots. Commits timestamped (see `git log`).

## Adding data

1. Pick domain dir (`funding-rates` / `lending` / `strategies`).
2. Create `<asset>/<protocol>/` leaf (add `<version>/` if protocol versioned).
3. Drop `data.json` (+ optional `data.csv`).
4. Commit with timestamp.
