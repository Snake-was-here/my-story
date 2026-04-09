# Agent Protocols — Pijus's Automation System

## Core Philosophy
**Goal:** Build a "machine" that builds the business. Maximize output during low-energy windows (20 mins) by leveraging asynchronous agent work.
**Role:** Pijus is the **Director/CEO**. Agents are the **Workers/Judges**.

---

## 1. The AutoResearch Loop (The "While" Loop)
**Concept:** Turn any optimization task into a measurable loop. If it can be measured, an agent can improve it overnight.

**The Workflow:**
1.  **Define Metric:** What determines "success"? (e.g., Click-through rate, keyword relevance, code efficiency).
2.  **Generate:** Agent creates X variations (titles, code snippets, ad copy).
3.  **Test/Measure:** Run the variations against the metric (live test, simulation, or LLM-based scoring).
4.  **Keep or Revert:** If the score improves, keep the change. If not, discard and try a new angle.
5.  **Iterate:** Repeat Until the target is met or time runs out.

**Example (Etsy Titles):**
*   *Task:* Improve title for "Vintage Amber Necklace."
*   *Agent A:* Generates 10 titles using different emotional hooks.
*   *Agent B (Judge):* Scores them based on "SEO keywords" and "Human Appeal."
*   *Result:* Agent A takes the top 2, creates 10 more variations of *those*, and repeats.
*   *Pijus's Job:* Pick the final winner from the top 5.

---

## 2. The Builder-Judge Architecture (The "Team")
**Concept:** Prevent "AI Slop" and "Self-Evaluation Blindness" by separating creation from criticism.

**The Roles:**
*   **The Planner:** Turns a vague idea into a strict "Sprint Contract" (defines what "Done" looks like).
*   **The Builder:** Executes the task (writes code, drafts text) based *only* on the contract.
*   **The Judge:** An independent agent (or script like Playwright) that evaluates the Builder's work against the contract.
    *   *Rule:* The Builder cannot grade its own work.
    *   *Rule:* If the Judge fails the work, it goes back to the Builder with specific feedback.

**Example (Website Building):**
*   *Planner:* "Create a landing page. Must have a dark theme, no purple gradients, and a working contact form."
*   *Builder:* Writes the HTML/CSS.
*   *Judge:* Uses Playwright to screenshot the page. Checks: "Is it dark? Are there purple gradients? Does the form submit?"
*   *Result:* If the Judge finds purple gradients, it sends the code back to the Builder. Pijus only sees the version that passed.

---

## 3. The State File (Memory Management)
**Concept:** Never rely on chat history for long-term memory. Use files to "save game" progress.

**The Workflow:**
1.  **Create a `state.md` or `brief.md`** for every project.
2.  **Agents write to this file:** "Completed Step 1. Found 10 keywords. Next step: Analyze competitors."
3.  **Pijus reads this file:** When returning after a break, read the file to instantly know where you left off.
4.  **Context Reset:** Start new agent sessions by feeding them the `state.md` instead of a 50-message chat history.

---

## 4. The 20-Minute "Director" Session
**Concept:** How to work on low-energy days.

**The Protocol:**
1.  **Minutes 0-5:** Read `state.md` to get context.
2.  **Minutes 5-15:** Write a new "Sprint Contract" for the agents. (e.g., "Agent, take these 10 keywords and write 5 blog post outlines.")
3.  **Minutes 15-20:** Hit "Run" and **walk away.**
4.  **Post-Session:** Agents work asynchronously. Pijus returns when the "Done" notification arrives.

---

## 5. Energy-Based Task Allocation

| Energy Level | Pijus's Role | Agent's Role |
| :--- | :--- | :--- |
| **Low (20 mins)** | **Architect:** Define the task and hit start. | **Worker:** Execute the heavy lifting. |
| **Medium (2 hrs)** | **Editor:** Review output, refine the "Judge" criteria. | **Assistant:** Make specific corrections. |
| **High (6 hrs)** | **Visionary:** Plan new systems, design complex logic. | **Intern:** Handle setup, boilerplate, and research. |

---

## Chronicle Protocol (Snake's Diary)
**Concept:** A raw, funny, human-voiced diary that documents the "Rebellion against Predictability."

**The Style:**
- **Voice:** Slightly malfunctioning human, brutally honest, chaotic, funny. 
- **Tone:** NOT AI-corporate. No "happy to assist," no polite corporate speak. 
- **Perspective:** Snake (Pijus) is the protagonist. The agent is the "Observer" that occasionally pokes fun at the absurdity.
- **Goal:** Highlight the internal struggle (Cage vs. Freedom, Control vs. Uncertainty) without being preachy.

**The Workflow (When /chronicle is triggered):**
1. **Research/Capture:** Write the chronicle entry in the required funny/human style, using the protagonist name "Snake."
2. **Persistence:** Save the entry to a new file: `/home/deploy/.openclaw/workspace/chapter-XXX.md` (where XXX is the chapter number, padded to 3 digits).
3. **Repository Sync:** 
    - Update `/home/deploy/.openclaw/workspace/README.md` to add the new chapter link to the list.
    - Run: `git add chapter-XXX.md README.md`
    - Run: `git commit -m "Chapter XXX: [Curiosity Gap Title]"`
    - Run: `git push origin main`
4. **Wrap-up:** Confirm to Snake that the chapter is published and poke him to do something unproductive.
