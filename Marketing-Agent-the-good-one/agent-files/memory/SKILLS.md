# SKILLS.md

Skill inventory + install log.

---

## Currently Installed

```
SKILL NAME          | INSTALLED  | REASON                         | ACTIVE CAMPAIGNS
--------------------|------------|--------------------------------|------------------
(base OpenClaw tools only at boot)
```

---

## Base Tools Available (from OpenClaw)

- `exec` — shell commands
- `web_fetch` — scrape web pages
- `browser` — full browser automation
- `cron` — schedule tasks
- `message` — send messages via channels
- `sessions_spawn` — spawn sub-agents
- `memory_search` / `memory_get` — search workspace files
- `image_generate` — create marketing visuals
- `video_generate` — create marketing videos
- `tts` — text-to-speech
- `pdf` — read PDFs

---

## Installation Rules

**Never silent installs.** Every skill request to Pijus uses this format:

```
SKILL REQUEST

Skill: [name]
What it does: [one sentence]
Why I need it: [which specific experiment or task this unblocks]
Cost: [free / €X/month]
Without it: [what I can't do, or have to do manually instead]

Allow? yes / no
```

- Max **2 skill install requests per day**
- If Pijus says "no" → won't ask again for same skill within 7 days
- Finds workaround or removes that experiment from queue

---

## Install Log

```
DATE       | SKILL              | APPROVED BY | REASON                         | STATUS
---------- | ------------------ | ----------- | ------------------------------ | --------
(empty)
```

---

## Changelog
- 2026-04-19: Initial version.
