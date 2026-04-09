# Plan: Moltbook Content Automation System
**Date:** 2026-03-31
**ETA:** 4-6 hours build + 1 week testing

## Goal
Fully automated pipeline: Reddit (r/moltbook) → AI text → Minecraft parkour video → Buffer → TikTok/Instagram/YouTube

## Phase 1: Output Definition (What "Done" Looks Like)
1. Daily cron job pulls top N posts from r/moltbook
2. Filters by engagement/upvotes to find "best performing"
3. Extracts post title/body → sends to AI for rewrite
4. Generates 60s-90s video: Minecraft parkour gameplay + dynamic subtitles
5. Auto-schedules to Buffer with platform-specific formatting
6. Sends confirmation + dashboard by Telegram

## Phase 2: Step Extraction

### Step A: Reddit Content Pipeline
**ACTION:** Setup Reddit API integration
**TOOl:** PRAW (Python Reddit API Wrapper) OR Serper/Scrapling
**OUTPUT:** Daily dump of top posts with metadata (upvotes, comments, score)
**Gate:** Reddit auth required (app credentials)

### Step B: Content Filter & Select
**ACTION:** Parse top posts, rank by engagement/velocity
**Tool:** Python script (n8n or local)
**OUTPUT:** Selected post ID + text content

### Step C: Text Processing
**ACTION:** Rewrite post for video format (hook + body)
**Tool:** OpenAI/Claude API
**OUTPUT:** 60-90 second script with timestamps

### Step D: Video Generation
**ACTION:** Render video with Minecraft parkour + generated subtitles
**Tool:** FFmpeg + MoviePy OR CapCut API if available
**Options:**
- A: Pre-recorded Minecraft parkour library (local files)
- B: Download from YouTube (copyright risk)
- C: Use existing CC0 Minecraft gameplay
**OUTPUT:** Final video file (1080x1920 portrait)

### Step E: Buffer Integration
**ACTION:** Schedule video across platforms
**Tool:** Buffer API (Create Buffer account first if needed)
**OUTPUT:** Scheduled posts with platform-specific captions

### Step F: Notification & Logging
**ACTION:** Send success+stats to Telegram, log to file/Notion
**Tool:** Telegram bot + n8n/OpenClaw
**OUTPUT:** Daily digest

## Phase 3: Dependency Mapping

```
A. Reddit API ──┐
                ├──→ C. AI Rewrite ──→ D. Video ──→ E. Buffer ──→ F. Notify
B. Filter ───────┘                    ↑
                                      │
                Pre-recorded gameplay ─┘
```

**Sequential blocks:** C needs A output, D needs C output, E needs D output
**Parallel:** Minecraft assets can be gathered any time before D

## Phase 4: Resource Inventory

### Have
- OpenClaw (this system)
- n8n (automation)
- PC with FFmpeg capability
- Telegram for notifications

### Need (Auth/API)
| Item | How | Cost | Blocker? |
|------|-----|------|----------|
| Reddit API credentials | reddit.com/prefs/apps | Free | Register app |
| OpenAI API key | platform.openai.com | Pay-per-use (~$0.002/req) | None |
| Buffer account | buffer.com | Free tier: 3 platforms, 10 posts queued | Instagram requires Business/Creator account |
| Buffer API token | buffer.com/developers/apps | Free | Apply for developer access |
| Minecraft parkour clips | YouTube Creative Commons OR pre-record | Time | Copyright risk if not CC0 |

### Blockers to Resolve
1. **Instagram via Buffer** requires Business/Creator account + Facebook link. Do you have this?
2. **Copyright:** Minecraft parkour — DIY recording or verified CC0 source?
3. **OpenAI vs local:** Could use local LLM (Ollama) to save $, but language quality may drop.

## Phase 5: Validation Checkpoints

**Test 1 (Day 1):** Can we fetch r/moltbook top posts? → `/moltbook-test-reddit`
**Test 2 (Day 1):** Can we generate one video with hardcoded text? → `/moltbook-test-video`
**Test 3 (Day 2):** Does Buffer API accept uploads? → `/moltbook-test-buffer`
**Test 4 (Day 3):** Full chain: fetch → generate → schedule

## Build Phases

### Phase 0: Asset Gathering (Do First)
- [ ] Source/upload 10-20 Minecraft parkour clips (10-15s each)
- [ ] Verify you have Buffer + Instagram Business account linked
- [ ] Get Reddit API credentials
- [ ] Get OpenAI API key

### Phase 1: Reddit Scraper (30 min)
- [ ] Python script using PRAW or Scrapling
- [ ] Output: JSON with posts (title, selftext, score, ups, num_comments)
- [ ] Filter: score > threshold, exclude deleted/removed

### Phase 2: Content Processing (30 min)
- [ ] n8n/OpenClaw webhook to receive posts
- [ ] AI rewrite script (hook + 3-4 key points)
- [ ] Output: structured JSON with timestamps

### Phase 3: Video Builder (2-3 hours)
- [ ] FFmpeg + MoviePy pipeline
- [ ] Select random background clip(s)
- [ ] Generate SRT subtitles from text + timestamps
- [ ] Render 1080x1920 @ 30fps

### Phase 4: Buffer Scheduler (1 hour)
- [ ] Buffer API: Upload media
- [ ] Create posts for each platform
- [ ] Set schedule (next available slot)

### Phase 5: Cron + Notification (30 min)
- [ ] Daily trigger (cron)
- [ ] Telegram notification on success/failure
- [ ] Simple dashboard (Notion or Markdown)

## Risk Mitigation

| Risk | Workaround |
|------|-----------|
| Buffer API flaky | n8n has Buffer node — test first |
| Video render slow | Async processing + queue |
| Copyright strikes | Only use pre-recorded or CC0 gameplay |
| OpenAI rate limits | Local LLM fallback |
| Reddit rate limits | PRAW handles this automatically |

## Quick Wins (Do First)
1. Verify Buffer can post to all 3 platforms from your account
2. Check Reddit API access from your IP
3. Confirm FFmpeg/moviepy works on your VPS

## Decision Gates

**Gate 1:** Do you have Instagram Business/Creator account? (Required for Buffer)
→ If no: Skip Instagram or upgrade account

**Gate 2:** Do you have Minecraft Java + can record? (Or prefer CC0 library?)
→ If yes: Record 10 clips yourself (cleanest)
→ If no: Use Creative Commons sources (need attribution in desc)

**Gate 3:** Budget for OpenAI? (~$5-10/month at low volume)
→ If no: Use local LLM via Ollama

## Next Actions
Reply with answers to Gates 1-3, then I'll spawn Phase 1 build.