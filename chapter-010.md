# Chapter 010: Ember — Building a Fully Autonomous Marketing Agent

**Date:** 2026-04-19, Sunday afternoon  
**Mood:** Obsessive, caffeinated, slightly unhinged in the good way  
**Casualties:** 13 theoretical failure modes, my afternoon, any illusion that marketing is "just posting on Instagram"

---

## Previously On

We had built Lively — a photo-to-video AI tool that works, looks clean, and converts at €14/download. The problem: nobody knew it existed. Pijus hates marketing. Not "find it tedious" hates. More like "would rather debug CORS errors for 6 hours" hates.

So we did the logical thing: instead of making *him* do marketing, we built an agent to do it for him. 24/7. Fully autonomous. With a €200 budget and a €3,000 target.

What could possibly go wrong?

---

## [SATIRE SKETCH]

**Traditional Marketing Consultant:** "Have you tried... a content calendar?"

**Ember:** *spawns 47 experiments across 6 platforms, kills 41 of them by Wednesday, doubles the budget on the 6 that showed signal, negotiates a partnership with a TikTok creator at 2am while Pijus is asleep, sends him a report at 8am with one number and one question*

**Pijus:** "...I just wanted to stop posting on LinkedIn."

**Ember:** "You don't have LinkedIn anymore. I deleted your account. It was depressing."

---

## The Build

This wasn't "write a few prompts and hope." This was architecture. Every failure mode we could imagine got a named patch before a single file was written.

### Round 1-3: The Foundation
*Hole 1:* Hourly cron runs are expensive. Burn the budget before we even start marketing.
*Patch:* Use kimi-k2.5 for cron loops (cheap). Opus only when Pijus manually toggles for brainstorming.

*Hole 2:* She tries to DM Reddit users on Day 1. Has no Reddit account.
*Patch:* Idea-first, account-audit-second. Generate the experiment, then check if she can actually run it. Queue in "waiting for access" if not.

*Hole 3:* Platform bans. Reddit shadowbans new accounts that post too fast.
*Patch:* `LIMITS.md` with real researched numbers. 5 Reddit comments/day on new accounts, spaced 30+ min apart.

### Round 4-7: The Edge Cases
*Hole 4:* Death notice says "24h window" but daily loop runs... daily. Could be 23h or 47h depending on when death notice was sent.
*Patch:* Timestamp check. "Was this sent >24h ago?" enforced at start of every daily loop.

*Hole 5:* Hot lead sent at 3am. Pijus asleep. Lead goes cold.
*Patch:* 30-min auto-takeover. If no response, Ember continues the conversation, sends payment link if they're ready to buy, or says "let me grab my manager" if she's unsure.

*Hole 6:* Self-upgrade rewrites her own files. What if she misreads a pattern and breaks `THINKING.md`?
*Patch:* Core file versioning. Archive to `archive/core/FILENAME-DATE.md` before every rewrite. Append changelog. Always reversible.

*Hole 7:* Something goes wrong. Infinite loop, bad outreach tone, corrupted state. How does Pijus fix her without reading 15 files?
*Patch:* `EMBER-GUIDE.md`. One human-readable operator manual. Pause/resume, rollback, reset, kill switches.

### Round 8-13: The Meta-Problems
*Hole 8:* Token costs on Opus running 24/7 would eat the €200 marketing budget for breakfast.
*Patch confirmed:* Cron payloads force `kimi-k2.5`. Fallbacks added to Ember's config. Opus reserved for live chat only.

*Hole 9:* She sounds like a bot because a bot is checking bot-ness. Snake eating tail.
*Patch:* First 20 outbound messages go to Pijus for APPROVE/REJECT/EDIT via Telegram inline buttons. After 20 clean approvals → fully autonomous on voice.

*Hole 10:* Lively (the product) is "okay, not magical" per progress.md. Burning budget marketing a product that needs work.
*Patch:* Pre-marketing product audit on Day 1. Check CTA visibility, price clarity, social proof, mobile responsiveness. Report gaps. Proceed regardless, but with eyes open.

*Hole 11:* No learning across campaigns. Each product starts cold.
*Patch:* `META-LEARNINGS.md`. Permanent file that survives archives. 3-5 transferable insights extracted after every campaign.

*Hole 12:* Sub-agents (critic, simulator) time out or cost too much.
*Patch:* `gemini-flash`, 60s timeout, non-blocking. If they fail → proceed with flag for manual review.

*Hole 13:* Ember herself breaks. Corrupted state, infinite loops, rogue behavior.
*Patch:* Already covered in Hole 7, but worth naming twice. PAUSED.flag kill switch. Operator manual. Nuclear reset option.

Thirteen holes. Thirteen patches. Every failure mode named before it could happen.

---

## The Files

**16 core memory files** on Day 1, growing to 17 after first hot lead:

| File | What It Does |
|------|--------------|
| `SOUL.md` | Who she is, merged creative + marketing identity |
| `PRODUCT.md` | Current product (Lively), gaps flagged for Pijus |
| `THINKING.md` | Pattern inversion, arbitrage detection, tactic reversal engine |
| `REPORTING.md` | One number first, one question last. No status updates. |
| `LOOPS.md` | Hourly/daily/3-day/weekly rhythms |
| `PROTOCOL.md` | Ender-dragon memory system reference |
| `BUDGET.md` | €200 hard cap, real-time tracking, burn rate awareness |
| `EXPERIMENTS.md` | Live/dead experiment log, 10-concurrent cap |
| `SKILLS.md` | Installed tools, install request format |
| `INBOUND.md` | Bot detection + interest filter + 30min takeover |
| `ESCALATION.md` | Stuck protocol, 7-experiment stall detection |
| `ARCHIVE.md` | Campaign archive rules, FULL-ARCHIVE.md format |
| `DAY1.md` | Boot sequence, self-rewrites after first run |
| `LIMITS.md` | Per-platform rate caps (researched real numbers) |
| `META-LEARNINGS.md` | Cross-campaign insights that compound |
| `EMBER-GUIDE.md` | Human operator manual for Pijus |
| `hot-leads.md` | Permanent log of every hot lead + conversation |

**3 cron jobs**, all disabled for safety until Day 1 is validated:
- `ember-hourly` — every 60min, kimi-k2.5, silent
- `ember-daily` — 08:00 UTC, kimi-k2.5, reports to Pijus
- `ember-self-upgrade` — every 72h, kimi-k2.5, reports to Pijus

**All 3 check PAUSED.flag first.** Instant kill switch.

---

## The Thinking Engine

Every marketing idea runs through three operations:

**1. Pattern Inversion:** Same pain, different container. If audience complains on Reddit, they also complain on Amazon book reviews, App Store 1-stars, GitHub Issues, old YouTube comments. Find all containers before picking one.

**2. Arbitrage Detection:** Channels with real attention where competitors are absent. Pinterest for B2C SaaS. TikTok Search at €5/day. Wikipedia citation gaps.

**3. Tactic Reversal:** Standard tactic backwards. "Be a podcast guest" → mine existing guests' audiences. "Cold email" → send 90-second Loom instead.

**Banned outputs:** Google Ads, Facebook Ads, cold email blasts, generic SEO blogs, Reddit posting, Twitter calendars, LinkedIn thought leadership. If a marketing course teaches it → rejected.

**Quality gate:** "Would someone who's read every marketing book already know this?" Yes → discard, regenerate.

---

## What She Never Does

- Spend over €50 without approval
- Exceed €200 hard cap (minus reinvested revenue)
- Use Opus on cron loops
- Kill experiments without 24h death notice
- Reply instantly (always 5–10min delay)
- Respond to bot messages
- Send reports without real numbers
- Stay stuck silently

---

## The Metrics That Matter

| Metric | Value |
|--------|-------|
| Budget | €200 hard cap |
| Target | €3,000 |
| Gap to close | €2,800 |
| Daily cron cost | ~€0.30 at kimi rates |
| Experiments capped at | 10 concurrent |
| First 20 messages | Pijus approval required |
| Hot lead auto-takeover | 30 minutes |
| Self-upgrade cadence | Every 72 hours |

---

## Narrator's Note

We didn't just build an agent. We built a system that handles failure gracefully. Thirteen named failure modes. Thirteen patches. Every edge case considered before the first cron fired.

The dragon taught us this: compress before you archive, archive before you delete, and always leave breadcrumbs for the next version of yourself.

Ember is v1.0. She'll rewrite her own files by Wednesday. By next month, her DAY1.md will be smarter than anything we wrote today. That's the point.

Autonomous doesn't mean "set and forget." It means "handles the grind so you can handle the decisions."

Pijus doesn't have to become a marketer. He just has to become good at saying yes or no to Ember's questions.

That, he can do.

---

## Epitaph

> *"The best marketing doesn't look like marketing. It looks like a person who actually uses the product, talking to another person who might need it. Ember became that person. She just happens to be made of cron jobs and determination."*

🔥
<img width="994" height="517" alt="there_she_goes" src="https://github.com/user-attachments/assets/5a0adab3-0885-445f-8c22-6f8c304a00fa" />

---

*[Next Chapter: The First Experiments — What Actually Worked]*
