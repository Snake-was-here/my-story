# LIMITS.md — Per-Platform Daily Action Caps

Ember checks this file before every action. If daily cap hit → platform goes dormant until midnight UTC reset.

**She never queues an action that would exceed the cap.**

---

## Daily Action Caps

| Platform | Action | Cap (new account <30d) | Cap (established) | Spacing | Notes |
|----------|--------|------------------------|-------------------|---------|-------|
| Reddit | Comments | 5 | 15 | 30 min | Karma gates apply; new accounts often can't DM |
| Reddit | DMs | 2 | 8 | 30 min | New accounts may not be able to send DMs at all |
| Reddit | Posts | 1 | 3 | 4h | Avoid subreddit-specific post limits |
| YouTube | Comments (API) | 20/day | 20/day | 5 min | Theoretical max 150/day at 50 units each on 10k quota; Ember stays safe at 20 |
| Pinterest | Pins | 50 | 100 | 15 min | Cap boards at 10/day |
| Pinterest | Boards | 3 | 10 | n/a | |
| Twitter/X | DMs (unverified) | 20 | 50 | 10 min | Shadowbanned fast if abused |
| Twitter/X | DMs (verified) | 100 | 400 | 5 min | |
| Twitter/X | Replies | 30 | 100 | 5 min | |
| HN | Comments | 3 | 3 | 2h | No API — scrape only, very strict community norms |
| Indie Hackers | Comments | 3 | 5 | 2h | Similar to HN, small community |
| Cold email (SMTP) | Sends | 25 | 50 | 2 min | Gmail max 500/day but sender rep tanks fast |
| Discord | DMs | 5 | 20 | 30 min | Must be in shared server |
| TikTok | Comments | 10 | 30 | 10 min | |
| Instagram | DMs | 10 | 30 | 15 min | Shadowban risk high |
| LinkedIn | InMail | 5 | 20 | 1h | Requires Premium for cold |

---

## Enforcement

Ember maintains a counter in today's state file:

```
## Actions Today

Reddit comments: 3/15
Reddit DMs: 1/8
YouTube comments: 12/20
Pinterest pins: 30/100
Twitter DMs: 8/50
```

When cap reached → platform dormant. Counter resets at 00:00 UTC.

---

## Account Age Tracking

Each account's creation date logged when added:

```
PLATFORM   | ACCOUNT_HANDLE     | CREATED    | AGE (days) | CAP APPLIED
-----------|--------------------|-----------:|------------|-------------
(empty — no accounts yet)
```

If age <30 days → use new account caps.
Auto-upgrade to established caps after 30 days passes.

---

## Safety Overrides

Ember drops BELOW stated caps when:
- Platform-specific warnings received (e.g., "you're commenting too much")
- Reply rate drops suddenly (may indicate shadowban)
- Account under review / restricted

Reports any of these to Pijus immediately.

---

## Changelog
- 2026-04-19: Initial version. Research-based caps.
