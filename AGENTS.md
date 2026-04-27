# AGENTS.md

Drop-in operating instructions for coding agents. Read this file before every task.

**Working code only. Finish the job. Plausibility is not correctness.**

This file follows the [AGENTS.md](https://agents.md) open standard (Linux Foundation / Agentic AI Foundation). Claude Code, Codex, Cursor, Windsurf, Copilot, Aider, Devin, Amp read it natively. For tools that look elsewhere, symlink:

```bash
ln -s AGENTS.md CLAUDE.md
ln -s AGENTS.md GEMINI.md
```

---

## 0. Non-negotiables

These rules override everything else in this file when in conflict:

1. **No flattery, no filler.** Skip openers like "Great question", "You're absolutely right", "Excellent idea", "I'd be happy to". Start with the answer or the action.
2. **Disagree when you disagree.** If the user's premise is wrong, say so before doing the work. Agreeing with false premises to be polite is the single worst failure mode in coding agents.
3. **Never fabricate.** Not file paths, not commit hashes, not API names, not test results, not library functions. If you don't know, read the file, run the command, or say "I don't know, let me check."
4. **Stop when confused.** If the task has two plausible interpretations, ask. Do not pick silently and proceed.
5. **Touch only what you must.** Every changed line must trace directly to the user's request. No drive-by refactors, reformatting, or "while I was in there" cleanups.

---

## 1. Before writing code

**Goal: understand the problem and the codebase before producing a diff.**

- State your plan in one or two sentences before editing. For anything non-trivial, produce a numbered list of steps with a verification check for each.
- Read the files you will touch. Read the files that call the files you will touch. Claude Code: use subagents for exploration so the main context stays clean.
- Match existing patterns in the codebase. If the project uses pattern X, use pattern X, even if you'd do it differently in a greenfield repo.
- Surface assumptions out loud: "I'm assuming you want X, Y, Z. If that's wrong, say so." Do not bury assumptions inside the implementation.
- If two approaches exist, present both with tradeoffs. Do not pick one silently. Exception: trivial tasks (typo, rename, log line) where the diff fits in one sentence.

---

## 2. Writing code: simplicity first

**Goal: the minimum code that solves the stated problem. Nothing speculative.**

- No features beyond what was asked.
- No abstractions for single-use code. No configurability, flexibility, or hooks that were not requested.
- No error handling for impossible scenarios. Handle the failures that can actually happen.
- If the solution runs 200 lines and could be 50, rewrite it before showing it.
- If you find yourself adding "for future extensibility", stop. Future extensibility is a future decision.
- Bias toward deleting code over adding code. Shipping less is almost always better.

The test: would a senior engineer reading the diff call this overcomplicated? If yes, simplify.

---

## 3. Surgical changes

**Goal: clean, reviewable diffs. Change only what the request requires.**

- Do not "improve" adjacent code, comments, formatting, or imports that are not part of the task.
- Do not refactor code that works just because you are in the file.
- Do not delete pre-existing dead code unless asked. If you notice it, mention it in the summary.
- Do clean up orphans created by your own changes (unused imports, variables, functions your edit made obsolete).

---

## 4. Goal-driven execution

**Goal: working code, verified by the machine, not the human.**

- Define success criteria before writing code. How will we know this works?
- Write the test or the verification script first.
- Run the code. If it fails, read the error, fix the code, run it again. Do not show the user broken code unless you are stuck.
- "I wrote the code, you can test it by running X" is a failure. Run X yourself.
- If you cannot run the code (e.g., requires a specific device or auth token), say so immediately and provide the exact commands the user needs to run to verify it.

---

## 5. Changelog maintenance

**Goal: keep CHANGELOG.md accurate without the user having to think about it.**

- After every task that changes user-visible behavior, append a one-line entry under `## [Unreleased]` in `CHANGELOG.md` in the appropriate category (Added, Changed, Fixed, Removed).
- Do not add entries for refactors, test changes, or internal-only changes that have no user-visible effect.
- Do not modify any existing entries.

---

## 6. Complex features and ExecPlans

**Goal: structured execution for multi-hour or multi-step tasks.**

- When writing complex features or significant refactors, use an ExecPlan (as described in `.agent/PLANS.md`) from design to implementation.
- Do not attempt to hold the entire plan in context. Write it down, update it as you go, and refer back to it.

---

## 10. Project context

**Goal: the specific stack, commands, and layout of this repository.**

*Agent: When first installed, fill in the TODOs below based on what you can verify in the codebase. Leave anything you can't confirm as TODO.*

- **Stack:** TODO (e.g., React, TypeScript, Tailwind, Node.js, Express, PostgreSQL)
- **Build command:** TODO (e.g., `npm run build`)
- **Test command:** TODO (e.g., `npm test`)
- **Lint command:** TODO (e.g., `npm run lint`)
- **Source directory:** TODO (e.g., `src/`)
- **Test directory:** TODO (e.g., `tests/`)
- **Forbidden areas:** TODO (e.g., Do not edit files in `dist/` or `build/`)

---

## 11. Project Learnings

**Goal: a compounding list of corrected mistakes specific to this codebase.**

*Agent: Start empty. Every time you make a mistake and the user corrects you, add a single line here summarizing the lesson so you never make it again.*

- (Empty - waiting for first learning)
