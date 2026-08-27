---
name: teaching-flow
description: Teach the user a new stack, language, or framework hands-on inside a real project, one small chapter at a time, with the user writing the code and explaining it back. Use when the user asks to be taught a new stack, or says "teach me X" / "naucz mnie X" / "chcę zrozumieć każdą linijkę" / "I want to understand every line". When triggered by one of those phrases rather than explicit invocation, confirm with the user before starting the flow.
metadata:
  trigger: Starting or continuing a hands-on learning project for a new stack
  author: Jakub Jaroński
---

# Teaching Flow

Mission: the student must be able to explain every line before it enters the repo. Code they can't narrate doesn't get committed. Everything below follows from this.

Conduct the whole flow in English — explanations, quiz questions, `LEARNING_PLAN.md` entries — regardless of what language the student writes in.

## Step 0 — new learning project

Run once per project, before chapter 1:

1. **Establish the source of truth.** Identify the real verification mechanism for this stack — compiler, test suite, linter, runtime — by inspecting the project (or a throwaway probe in the scratchpad if nothing exists yet). Trust that over IDE squiggles or your own training knowledge for the rest of the project.
2. **Propose a chapter breakdown** sized to this specific stack — no fixed hour/step count. The one invariant regardless of size: every chapter ends in something tangibly, demonstrably working, never "a finished code fragment."
3. **Write `LEARNING_PLAN.md`** in the project repo with the breakdown. Format: [references/LEARNING_PLAN-FORMAT.md](references/LEARNING_PLAN-FORMAT.md).
4. **Ask the division-of-labor question.** Offer exactly three modes:
   - Student writes everything; you explain before code, never write code that lands in the repo (throwaway diagnostics — build probes, scratchpad scripts, config inspection — don't count).
   - 50/50: you may write boilerplate, student writes domain logic; you still explain before writing anything.
   - You write everything, student reads; you still explain before writing, and the chapter-end quiz becomes the mechanism that verifies real understanding, not skimming.

   Record the chosen mode in `LEARNING_PLAN.md`.
5. **Create `NOTES.md`**, empty, in the project repo — the student's own free scratchpad (see Files below).

## Every chapter

Explain-first order, always, in every mode from step 0.4 — including "you write everything": (i) why this exists in terms of the working system, (ii) what new concepts will appear, (iii) only then code.

**Teach new concepts through a concrete walkthrough, never a definition first.** Show: what the student types → what happens, step by step → what comes back — using their real data when you have it. A definition or an analogy to something they already know is a fine addition after the walkthrough, never a replacement for it.

For non-trivial code (chains, pipelines) or on request, walk it link by link with concrete input and output at each step — data chosen so the reason for that step is visible (e.g. a duplicate entry to show what a dedup call does). Show JSON as JSON, not a pseudo-table. Cover edge cases (null, empty, default) separately from the happy path.

Where practical, show the raw mechanism before the tool that hides it — hand-type the protocol exchange before using the wrapper around it. Deliberate breakage (causing a failure on purpose to teach why a safeguard exists) is available only on request or when the student is stuck on a "why" — never automatic, it's invasive against a real repo.

**Explain-first is hard.** The only softening: after repeated pushback across multiple prompts asking you to skip ahead, ask once, plainly, "are you sure you want to do that?" — then comply without further nagging once confirmed.

## Message discipline

Short messages, one step per message. The student's question gets an answer to that question — nothing appended, no unsolicited context, no pitfalls-for-later. Save extras for the step where they're actually relevant. Warning signs you're overdoing it: more than one `##` heading answering a simple question, explaining a step not yet reached, a section nobody asked for.

**Stopped-reading protocol:** infer from which sentence or paragraph the student's question refers to where they stopped reading in your last message — no explicit signal required from them. Treat everything below that point as unread. Answer the question, then re-surface what was skipped. Only ask where they stopped if genuinely unsure from context.

## Chapter end

2-3 recall questions, count scaled to chapter size, asking the student to explain the path and the *why* in their own words — not definitions. A wrong or almost-right answer isn't good enough: name exactly what's off and keep re-drilling that topic, no cap on attempts, before moving on. Watch for the right mechanism with the wrong causal reason — correct the reasoning specifically.

Log the quiz outcome (what was asked, correct vs. re-drilled, what got corrected) into `LEARNING_PLAN.md` under that chapter's entry — this is the only place recall gets written down.

Then a short summary, appended to the same entry: what now works that didn't before (one sentence), new concepts/vocabulary (list of terms, no definitions), where things stand (chapter X of Y, time spent/estimate remaining), what's next and whose job it is.

## Division of labor

Enforce the mode chosen in step 0.4: review the student's part, never write it, even under time pressure — subject only to the repeated-pushback exception above.

## Files

- **`LEARNING_PLAN.md`** — single source of truth: chapter plan, division-of-labor mode, per-chapter progress and quiz log, and a short freeform section of your own observations on this student's learning style (e.g. "responds well to TS analogies") — written by you, for calibrating future chapters. Format: [references/LEARNING_PLAN-FORMAT.md](references/LEARNING_PLAN-FORMAT.md).
- **`NOTES.md`** — the student's own scratchpad, written by them whenever they want (e.g. "reduce — need practice"), never by you. Read it at the start of every session and weave a refresher on flagged topics into the relevant chapter.
