# EXPERIMENTS.md

Live experiment tracking + death log.

---

## Active Experiments (MAX 10 per product)

```
ID | NAME                          | STARTED    | CHANNEL          | STATUS     | SPEND | SIGNAL
---|-------------------------------|------------|------------------|------------|-------|----------
(empty — Day 1 not run yet)
```

**Rule:** If 10 slots filled → hourly loop does monitoring + research only, no new launches until one dies.

---

## Queue (waiting for slot, approval, or access)

```
ID | NAME                          | CHANNEL          | NEEDS                          | ESTIMATED SETUP
---|-------------------------------|------------------|--------------------------------|-----------------
(empty — awaiting Day 1 boot)
```

---

## Signal Thresholds (minimum to keep alive)

| Channel | Min Signal | Window |
|---------|-----------|--------|
| Reddit / forum comment | 3 profile clicks | 48h |
| Cold DM | 1 genuine reply | 48h |
| YouTube comment | 5 clicks | 72h |
| Email outreach | 1 open + click | 72h |
| Paid ad (if approved) | 2 conversions | €20 spend |
| SEO / free tool | Indexed | 7d, evaluate at 30d |
| Pinterest pin | 20 saves | 72h |
| TikTok organic | 1,000 views | 48h |

Below threshold = death notice, 24h window, then killed.

---

## Death Notice Tracking

Each death notice has a timestamp. At start of every daily loop:
- "Was this notice sent >24h ago with no Pijus reply?" → kill it
- Log to dead experiments section

---

## Dead Experiments (permanent log — prevents repeats)

```
ID | NAME                          | KILLED     | CHANNEL          | FINAL RESULTS                  | HYPOTHESIS
---|-------------------------------|------------|------------------|--------------------------------|------------
(empty — no deaths yet)
```

**Critic sub-agent checks this list on every new idea. If duplicate → rejected.**

---

## Changelog
- 2026-04-19: Initial version.
