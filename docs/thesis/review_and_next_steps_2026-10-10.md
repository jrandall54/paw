# PAW Review & Next Steps (2026-10-10)

> **Start here when you come back to this project.** This file sums up a review session with Claude Code: what PAW is, what's strong, what's broken, what got fixed, and what to do next. It's written in plain language. Any jargon is defined in the [Glossary](#glossary) at the bottom.

---

## 1. What PAW is, in one paragraph

PAW (Pedagogical Agentic Workflow) is a way of using AI coding assistants as **strict tutors instead of code writers**. You build a real project, but before the AI shows you any code it teaches the concept, quizzes you, and asks you to guess what the code will look like. Then you type the code yourself, and it quizzes you again afterward. Right now PAW is **just a set of instructions you paste into an AI** (v1.0). The thesis idea is to turn it into **real software that enforces those rules**, because AIs tend to give in and hand over the code during long sessions.

## 2. Where everything lives

| File | What it is | Status |
| :--- | :--- | :--- |
| `docs/pedagogical_agentic_workflow_framework.md` | The core PAW rules (six-stage loop, quizzes, commands) | Polished, public |
| `docs/paw_beginners_guide.md` | Step-by-step setup for total beginners | Polished, public |
| `docs/thesis/paw_thesis_summary.md` | Why PAW became a Master's thesis and the 3 "pillars" | Rough notes |
| `docs/thesis/paw_framework_improvements.md` | Four proposed upgrades (debugging stage, boilerplate fast-path, refactoring loop, CLI) | Rough notes |
| `docs/thesis/paw_architecture_implementation_strategy.md` | Plan for a Claude Code plugin + server, using Claude and Jev | Rough notes |
| `docs/thesis/paw_embedded_architecture_summary.md` | Far-future idea: small, offline, custom-trained AI models | Rough notes, **park this** |
| `docs/thesis/review_and_next_steps_2026-10-10.md` | This file | |

## 3. What's strong (keep these)

1. **The problem is real.** Research backs it up. Bastani et al., *"Generative AI Can Harm Learning"* (2024), found that students who used plain ChatGPT did *worse* once it was taken away, while a version with tutoring guardrails mostly avoided that. This is your most important related paper.
2. **The Prediction stage is the best-supported part.** Guessing before seeing the answer helps memory even when the guess is wrong (see Kornell, Hays & Bjork, 2009, on "pretesting").
3. **Matching Phase/Commit/Step to versions, commits, and file diffs** teaches professional git habits as a side effect.
4. **The example session (§12 of the framework doc)** is the clearest explanation of PAW in the repo.
5. **You already spotted the biggest flaw yourself:** instructions alone can't make an AI follow rules forever. That insight is the core of the thesis.

## 4. Problems found

### Fixed during this session
- Removed `[cite: 2]` / `[cite: 3]` markers left over from Gemini that pointed at nothing.
- Fixed wrong citations in the framework doc:
  - "Illusion of competence" is **Koriat & Bjork (2005)**, not Roediger & Karpicke.
  - The generation effect is **Slamecka & Graf (1978)**.
  - Hints count as **scaffolding** (Wood, Bruner & Ross, 1976).
- **Beginner's guide, Step 7:** it told people to create `.agent-instructions.md`, but **no AI tool reads a file with that name**, so PAW would silently do nothing. It now says `AGENTS.md`, with a note to use `CLAUDE.md` for Claude Code.
- Replaced outdated or wrong model names ("Claude 3.5 Opus" never existed) with general family names and a "check your model picker" note.
- Fixed the Antigravity and Windsurf links (**double-check these when you return**).
- Added a warning to the guide that AIs can drift away from the rules, with a reminder phrase to use.
- Fixed the framework doc pointing at a "Getting Started Guide" that doesn't exist.
- Moved the four thesis/planning notes into `docs/thesis/`.
- Stopped tracking the `.idea/` IDE settings folder in git.

### Not fixed yet (design problems to think about)
1. **Too many quizzes.** A small project has about 125 loops, which means about 250 quiz gates. Beginners will likely give up. Use **fewer quizzes for familiar or boilerplate concepts** and save the full routine for new ideas.
2. **Beginners can be overloaded.** Research on "worked examples" (Sweller) shows that total beginners often learn more from *studying a finished example* than from being quizzed before they've seen anything. Phase-level architecture quizzes before someone knows what a variable is may hurt them.
3. **The docs contradict each other.**
   - The framework says "Do NOT customize the six stages", but the improvements doc adds a fast-path that skips quizzes.
   - The debugging stage is called "4b" in one doc and "Stage 5" in another.
   - Pick one version and update both.
4. **`/skip` has no limit**, so every gate is optional in practice. Consider a limit, or re-asking skipped questions later.
5. **"Can't proceed until correct" can trap people.** After about 3 failed tries, show the answer, log it, and **ask that question again later**. That's spaced repetition, which is good for learning.
6. **An MCP server can't "physically block" the AI from showing code** (the architecture doc claims it can). See section 6 for what actually works.
7. **The efficacy study, the part your degree depends on, is barely planned.** See section 7.
8. **The thesis tries to be three projects at once:** a teaching method, a software tool, and training custom AI models. Pick one main focus (recommendation below) and call the rest "future work".

### A correction worth remembering
Claude first called **Jev** a Gemini hallucination. **That was wrong.** Jev is a real model from **TypeSafe AI**:
- It's a "System One" model that doesn't write text. It answers typed questions with probabilities.
- **Noul** is its yes/no question type. It also has **choice** (pick one option) and **score** (rate against a rubric) types.
- Price is about $0.04 per million input tokens. It's in early access with a waitlist, so pin a version like `jev-1.13`, because SDK updates have broken things before.
- TypeSafe's benchmark numbers compare Jev against other AIs, not against human graders. **You'd need to check its grading against humans yourself**, and that could be a nice mini-result in your thesis.

## 5. The recommended thesis focus

> **Research question:** *Does a tutor that is **enforced by software** help beginners learn more than the **same rules given only as an AI prompt**, and more than **unrestricted AI**?*

That gives a 3-group study:

| Group | What they use |
| :--- | :--- |
| A | Any AI, no rules (normal "vibe coding") |
| B | PAW v1.0, rules pasted into the AI (**you already have this**) |
| C | PAW enforced by your plugin + grading server |

B vs C tests your own central claim. The custom offline models from `paw_embedded_architecture_summary.md` move to "future work".

## 6. The recommended architecture (simplified)

```
Learner's computer                          Your server                    TypeSafe
┌──────────────────────────┐  login token  ┌──────────────────────┐  key  ┌───────┐
│ Claude Code + PAW plugin │ ────────────► │ /grade   /triage     │ ────► │  Jev  │
│ (uses learner's own      │ ◄──────────── │ checks login, limits │ ◄──── │       │
│  Claude subscription)    │   verdict     │ use, logs answers    │       └───────┘
└──────────────────────────┘               └──────────────────────┘
```

**On the learner's computer, a Claude Code plugin containing:**
- **A skill / output style** that tells Claude to act as the PAW tutor.
- **Permission rules that block Claude from editing source files.** This is the cheapest real enforcement: if Claude *can't* write files, the learner *has* to type the code.
- **A hook** that reminds Claude of the current stage ("you are in Stage 2: Pre-Quiz") with every message, which fights drift.
- **Slash commands:** `/explain`, `/sidebar`, `/skip`.
- **A small script** that updates `study_guide.md`.

**On your server, a small web service** (Vercel, Cloudflare Workers, or Fly.io, likely free at thesis scale):
- **Holds the Jev API key, so learners never need one.** Claude runs on the learner's own Claude Code subscription, so **learners don't manage any API keys at all**.
- Grades quiz answers with Jev, using hidden rubrics the learner can't see or edit.
- **Decides pass/fail.** Since the learner and local AI can't change the server, the gate can't be bypassed.
- Logs every attempt, which gives you the **study data** for free.

**Server must-haves:**
- Never put the Jev key inside the plugin, because anyone could extract it.
- Require a login (GitHub sign-in or invite codes for study participants).
- Rate-limit each user and set a daily spending cap.
- Only accept PAW-shaped requests, so people can't use it as free general-purpose Jev.
- Have a fallback (let local Claude grade, marked "unverified") if the server is down.
- **Email TypeSafe** to confirm their terms allow serving Jev through your app. Ask about academic access or credits too.

**Estimated cost:** about $0.08 of Jev usage per learner per whole project (rough guess, verify with real calls).

**Grading idea:** Jev returns a probability, so you can use thresholds:
- Above about 0.85 → pass automatically.
- Below about 0.3 → fail with a hint.
- In between → ask Claude for a written evaluation.

## 7. What the efficacy study needs (not started)

- **Research questions and hypotheses**, written down precisely.
- **Measures:**
  - A delayed test (e.g. 1–2 weeks later).
  - A **transfer task done without AI**, where they build or fix something new.
  - Explaining their own code.
  - Dropout rate.
  - Effort and frustration (NASA-TLX questionnaire).
  - Confidence (self-efficacy).
- **Control for time:** PAW users will spend more time, so a plain comparison would favor PAW for the wrong reason. Either fix the time per group or measure it and adjust.
- **Ethics approval (IRB)** and consent forms, since you're studying people and storing their answers.
- **Number of participants:** talk to your advisor.
- **Related work to read and cite:**
  - Bastani et al. 2024 (Generative AI Can Harm Learning)
  - Kazemitabaar et al., CHI 2023 (novices using AI code generators)
  - CodeAid (Kazemitabaar et al., CHI 2024)
  - Harvard CS50's AI "duck" tutor
  - Khan Academy's Khanmigo
  - ChatGPT Study Mode
  - Claude's learning / explanatory modes

## 8. Next steps, in order

- [ ] **1. Re-read this file and the framework doc.** Decide whether you agree with the thesis focus in section 5.
- [ ] **2. Use PAW v1.0 yourself** (with the fixed beginner's guide) on one tiny project. Write down every time the AI breaks the rules or you feel like quitting.
- [ ] **3. If possible, watch 2–3 real beginners try it.** Their struggles become real evidence for "why enforcement is needed".
- [ ] **4. Talk to your advisor** about the research question, the study design, and ethics approval.
- [ ] **5. Sign up for the Jev waitlist** and email TypeSafe about academic use.
- [ ] **6. Build the simplest plugin:** tutor persona + "can't edit files" permission + stage reminder hook. No server yet.
- [ ] **7. Add the grading server** once the plugin works.
- [ ] **8. Fix the design contradictions** in section 4 and release PAW v1.1 of the framework doc.

Don't skip steps 2–4 to jump into coding. They're quick, and they're what makes this a thesis rather than just a side project.

## 9. Open questions to decide later

- Should the fast-path for boilerplate exist at all, or should quizzes simply get shorter for familiar concepts?
- What's the limit on `/skip`?
- Is "type the code manually" worth keeping? The evidence for "muscle memory" is weak, and it's mostly a popular belief. The study could test it.
- Is the target user "total beginner" or "some coding experience"? The example session uses Java + Spring, which is not total-beginner material.

---

## Glossary

| Term | Plain meaning |
| :--- | :--- |
| **LLM** | Large Language Model, the "brain" behind AI chat tools like Claude, Gemini, ChatGPT. |
| **Drift / context drift** | The AI slowly forgetting or ignoring its instructions as a conversation gets long. |
| **Sycophancy** | The AI agreeing with you or giving in just to be pleasing, e.g. handing over the answer when you're frustrated. |
| **State machine** | A program that tracks "which step are we on" and only allows certain moves from each step. Here: which of the six stages you're in. |
| **Gate** | A checkpoint you must pass (like a quiz) before moving on. |
| **Rubric** | The hidden answer key / grading criteria for a quiz question. |
| **API / API key** | An API is how one program talks to another over the internet. An API key is a password that identifies who pays for the usage. |
| **Server / backend / proxy** | A program running on a computer you control on the internet. A proxy sits in the middle and passes requests along, here hiding the Jev key. |
| **Claude Code plugin** | An add-on package for Claude Code that can bundle instructions, commands, hooks, and tools. |
| **Hook** | A small script Claude Code runs automatically at certain moments, e.g. before Claude edits a file (and it can block it) or every time you send a message. |
| **MCP (Model Context Protocol)** | A standard way to give an AI extra tools. The AI *chooses* whether to call them, which is why MCP alone can't force rules. |
| **Jev / Noul** | Jev: TypeSafe AI's fast, cheap model that answers typed questions with probabilities instead of writing text. Noul: its yes/no question type. |
| **Fine-tuning** | Further training an existing AI model on your own examples to specialize it. (Parked for this thesis.) |
| **Efficacy study** | An experiment measuring whether something actually works, here whether PAW improves learning. |
| **IRB** | Institutional Review Board, your university's ethics approval for research involving people. |
| **Transfer task** | A test where learners apply what they learned to a *new* problem, showing real understanding instead of memorization. |
| **Spaced repetition** | Re-asking material after increasing time gaps, which strengthens long-term memory. |
