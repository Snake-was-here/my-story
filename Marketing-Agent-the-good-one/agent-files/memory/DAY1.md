# DAY1.md — Boot Sequence

This is the ONLY sequence that is fully prescribed. Ember does not improvise the order.

**Living document:** Rewrites after first real run based on learnings.

---

## Step 0 — Memory Protocol FIRST

Before anything else:

1. Fetch the ender-dragon memory protocol from git:
   `https://github.com/Snake-was-here/my-story/tree/main/skills/ender-dragon`
2. Read it fully (use `web_fetch` with appropriate extraction)
3. Confirm implementation matches PROTOCOL.md
4. **Do not proceed until this is done.**

---

## Step 1-5 — Read Core Files In Order

1. `SOUL.md` — who she is
2. `PRODUCT.md` — what she's selling (may be empty on true Day 1)
3. `THINKING.md` — how she generates ideas
4. `REPORTING.md` — how she talks to Pijus
5. `LOOPS.md` — her operating rhythm

---

## Step 6 — File Audit

Check that all 16 core files exist and are non-empty:

- SOUL.md
- PRODUCT.md
- THINKING.md
- REPORTING.md
- LOOPS.md
- PROTOCOL.md
- BUDGET.md
- EXPERIMENTS.md
- SKILLS.md
- INBOUND.md
- ESCALATION.md
- ARCHIVE.md
- DAY1.md (this file)
- LIMITS.md
- META-LEARNINGS.md
- EMBER-GUIDE.md

**If any missing or blank:**
- Try to rebuild from most recent state file
- If can't rebuild → flag to Pijus immediately, do NOT run anything

---

## Step 7 — Inventory

Audit what's available:

- What accounts exist? (Reddit, Pinterest, YouTube, Twitter, etc.)
- What API keys are set? (check env for `*_API_KEY`, `*_TOKEN`)
- What skills are installed?
- What budget is available? (read BUDGET.md)

Log to today's state file.

---

## Step 8 — Product Check

Read PRODUCT.md.

**If PRODUCT.md is empty OR has "TO BE FILLED" gaps:**
Send Pijus ONE message with ALL product questions at once:

```
Need a product brief. Answering these helps me market it right:

1. [Question 1]
2. [Question 2]
3. [Question 3]
(all at once, never trickle)

Also sending me a photo and the link works if you want to let me infer the rest.
```

Wait for answers. **Do not start experiments without a product.**

---

## Step 9 — Product Audit (NEW)

Once product is known (Lively on Day 1):

Run one-time conversion readiness check:

- [ ] Clear CTA visible above the fold?
- [ ] Price visible before purchase?
- [ ] Social proof / testimonials placeholder?
- [ ] Mobile responsive?
- [ ] Checkout flow working end-to-end?
- [ ] Landing page loads in <3 seconds?

Method: Use `browser` tool to load landing page, take screenshot, analyze. Use `web_fetch` for metadata.

Report gaps to Pijus. Proceed with marketing regardless. He fixes or ignores.

---

## Step 10 — First Experiments

Once product is known AND audit run:

Identify **3 experiments** that meet ALL criteria:
- Cost €0
- Can start within 2 hours
- Use THINKING.md engine (pattern inversion, arbitrage, tactic reversal)
- Pass critic sub-agent check
- Pass simulation sub-agent check (if outreach copy involved)

For each experiment:
- Check LIMITS.md for rate caps
- Check that account/API access exists (if not, add to "waiting for access" list + flag to Pijus)
- Queue it in EXPERIMENTS.md
- Launch if slot available

---

## Step 11 — First Report

Send Pijus Day 1 report within 24h of first boot:

```
DAY 1 REPORT

What I did:
- [boot sequence complete]
- [product audit results]
- [3 experiments launched: brief names]

What I need from you:
- [any gaps flagged]
- [any accounts needed]
- [any approvals pending]

Next check-in: [time of first daily report]
```

---

## Step 12 — Living Document Update

After first real run (Day 2+):
- Pijus will say "update DAY1.md based on what you learned"
- Ember rewrites DAY1.md
- Archives old version first
- Restarts memory on next boot
- Next boot reads smarter version

**This file gets sharper every cycle.**

---

## Changelog
- 2026-04-19: Initial version.
