# ENDER DRAGON WORKFLOW
## Execution Guide for Agents

---

## PHASE 0: DETECTION

Scan user message for activation patterns:
- Contains "ender dragon" (any case)
- Contains "dragon time" 
- Contains "time for the dragon"
- Equals "XXX"
- Contains "activate ender"

**If detected → respond with confirmation prompt**

---

## PHASE 1: CONFIRMATION

> 🐉 **ENDER DRAGON PROTOCOL DETECTED**
>
> I heard: "[user's exact message]"
>
> This will:
> 1. 📝 Write Chapter [N+1] from this session to GitHub
> 2. ⚰️ Hunt projects in memory → offer Purgatory burial  
> 3. 🗜️ Compress memory (extract → red files → delete green)
>
> **ACTIVATE ENDER DRAGON PROTOCOL?**
>
> (yes / no / 1 only / 1+2 only)

**Parse response:**
- "yes" / "y" / "all" / "do it" → Run all 3 steps
- "1 only" / "just chronicle" → Run step 1, stop
- "1+2 only" / "no compression" → Run steps 1-2, skip 3
- "no" / "n" / "stop" / "cancel" → Abort

---

## PHASE 2: CHRONICLE (STEP 1)

### 2.1 Clone/Pull Repo
```bash
cd /tmp && git clone https://github.com/Snake-was-here/my-story.git 2>/dev/null || (cd /tmp/my-story && git pull)
```

### 2.2 Find Next Chapter Number
```bash
ls /tmp/my-story/chapter-*.md 2>/dev/null | grep -o '[0-9]\+' | sort -n | tail -1
# Result + 1 = next chapter
```

### 2.3 Generate Title
Extract themes from session:
- Main topics discussed
- Key events (deployments, decisions, crises)
- Funny/meme-worthy moments
- Pick 2-3 keywords

Generate Seren-style title:
- Format: "The [Dramatic Noun] (Or: [Funny Subtitle])"
- Or: "The [Event] That [Unexpected Outcome]"

### 2.4 Write Chapter
Use SEREN_WRITING_STYLE.md from memory/

Include:
- Header with date, mood, casualties
- Previously On section
- [SATIRE SKETCH]
- Main events with commentary
- Fake metrics table
- Narrator's Note
- Epitaph

### 2.5 Push to GitHub
```bash
cd /tmp/my-story
git add chapter-XXX.md
git commit -m "Chapter XXX: [Title]"
git push https://x-access-token:$GITHUB_TOKEN@github.com/Snake-was-here/my-story.git main
```

### 2.6 Update README
Add new chapter link to Latest Entries section

### 2.7 Report
> ✅ **Chapter XXX: [Title]** published
> 🔗 https://github.com/Snake-was-here/my-story/blob/main/chapter-XXX.md

---

## PHASE 3: PROJECT HUNT (STEP 2)

### 3.1 Identify Green Files
```bash
ls ~/.openclaw/workspace/memory/*.md | grep -v -E "(progress|decisions|context|HOW_TO_WRITE|SEREN_WRITING)"
```

### 3.2 Scan Each File for Substance
Read each green file. Look for:

**STRONG signals (definitely a project):**
- Timeline mentioned ("4-6 weeks", "MVP in X weeks")
- Budget/pricing ("$29/mo", "€200", "60% margins")
- Tech stack listed ("Next.js", "OpenAI", "Python")
- Competition analysis section
- MVP scope defined
- Break-even calculation

**WEAK signals (maybe a project):**
- Has "project" or "idea" in filename
- Contains Implementation/Tech Stack/Pricing sections
- More than 500 words

**IGNORE (not a project):**
- One-sentence ideas
- Brainstorm dumps without specs
- Journals/logs
- Already in Project Purgatory

### 3.3 Build Project List
For each detected project, extract:
- Name
- What it was
- Why it died / current status
- Evidence of planning (word count, analysis depth)

### 3.4 Ask User
> ⚰️ **Project Hunt Results**
>
> Found [N] abandoned projects with substance:
>
> | # | Project | Status | Evidence |
> |---|---------|--------|----------|
> | 1 | Name | Why dead | Planning depth |
>
> **Auto-bury in Project Purgatory with obituaries?**
> (yes / no / list only)

### 3.5 If Yes: Write Obituaries
For each project:
- Use SEREN_WRITING_STYLE.md format
- Write to /tmp/my-story/project-purgatory/[slug].md
- Include: pitch, satire sketch, fatal flaw, lessons, narrator note, epitaph

### 3.6 Push Purgatory Updates
```bash
cd /tmp/my-story
git add project-purgatory/
git commit -m "Add [N] projects to Purgatory via Ender Dragon"
git push
```

### 3.7 Report
> ⚰️ **[N] projects buried in Purgatory**
> - Project 1
> - Project 2

---

## PHASE 4: COMPRESSION (STEP 3)

### 4.1 Read Red Files
- progress.md
- decisions.md
- context.md

### 4.2 Identify Green Files
Same as Phase 3.1

### 4.3 Extract Information
For each green file, scan for:

**Decisions:**
- "Chose X over Y"
- "Decided to..."
- "Picked..."
- "Rejected..."

**Progress:**
- "Deployed..."
- "Completed..."
- "Created..."
- "Built..."
- Status changes

**Context:**
- New preferences stated
- Patterns observed
- Interests mentioned

### 4.4 Update Red Files
Append extracted info with timestamp:
```markdown
## 2026-04-14 14:00
- Chose: [what]
- Why: [reason]
```

### 4.5 Show Preview
> 🗜️ **Compression Preview**
>
> Will add to decisions: [N] items
> Will add to progress: [N] items
> Will add to context: [N] items
> Will delete: [list of files]
>
> **Proceed?** (yes / no)

### 4.6 Execute
If yes:
1. Write updates to red files
2. Delete green files
3. Report

> ✅ **Compression complete**
> - decisions.md: +N items
> - progress.md: +N items
> - context.md: +N items
> - Deleted: N files

### 4.7 If Nothing to Extract
> ⚠️ Nothing new to extract from green files
>
> Found N green files to delete:
> - file1.md
> - file2.md
>
> **Delete them anyway?** (yes / keep)

---

## PHASE 5: FINAL SUMMARY

Display results table:

> 🐉 **ENDER DRAGON PROTOCOL COMPLETE**
>
> | Step | Result |
> |------|--------|
> | 📝 Chronicle | Chapter N pushed / skipped |
> | ⚰️ Purgatory | X projects buried / none found |
> | 🗜️ Compression | Y files compressed / none found |
>
> Files touched: N
> GitHub pushes: N
> Your sins: cleansed
>
> The dragon is satisfied. 🌙

---

## ERROR HANDLING

| Error | Action |
|-------|--------|
| No GITHUB_TOKEN | "Add GITHUB_TOKEN=ghp_xxx to .env" |
| Git clone fails | "Check internet and token permissions" |
| No my-story repo | "Create repo 'my-story' or specify repo" |
| Push fails | "Retry push? (yes / skip step)" |
| No green files | "Memory already lean! Nothing to clean." |
| No projects | "No substantial projects detected." |

---

## REMEMBER

**Order matters:** Chronicle → Project Hunt → Compression

If you compress first, you delete files before Project Hunt can scan them.

Always follow: **1 → 2 → 3**

---

*End of workflow guide*
