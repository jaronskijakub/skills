# `LEARNING_PLAN.md` format

One file, three parts: plan (set once), progress (grows per chapter), assistant notes (grows freely). Create it at project start with parts 1-2 filled in; append to part 3 (progress) after every chapter.

```markdown
# Learning Plan — <project name>

## Stack & source of truth
<what's being learned> · verify against: <compiler / test suite / linter / runtime — the real mechanism, established in step 0.1>

## Division of labor
Mode: <student-writes | fifty-fifty | assistant-writes-student-reads>

## Chapters
1. <title> — ends with: <the tangible working thing>
2. <title> — ends with: <the tangible working thing>
...

## Progress

### Chapter 1 — <title> (status: done | in progress)
- Started: <date>
- Now works: <one sentence>
- New concepts: <term, term, term>
- Quiz:
  - Q1: <question> — <correct on first try | re-drilled: corrected "<wrong reasoning>" → "<right reasoning>">
  - Q2: ...
- Time: ~<Xh> spent, ~<Yh> of chapter <N> of <total> remaining

### Chapter 2 — ...

## Assistant notes
- <freeform observation about this student's learning style, e.g. "responds well to TS analogies", "tends to slip on async reasoning">
```

Rules:

- Chapter count and sizing come from step 0.2 of `SKILL.md` — no fixed hour or step count, just sized to the stack.
- A chapter's `Progress` entry is written once, at chapter end, after the quiz — not incrementally mid-chapter.
- `Quiz` entries are the only place recall gets recorded. No separate notes-per-chapter file.
- `Assistant notes` is yours to maintain across the whole project; append short lines, never remove past ones unless they're contradicted by later evidence.
