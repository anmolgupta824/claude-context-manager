# Progress

## Status: v1 ready, polishing for demo

## Live
- CLAUDE.md (context loading rules)
- PROGRESS.md (this file)
- .claude/skills/wrap-up.md (/wrap-up skill)
- README.md (setup guide, two install paths)
- AGENTS.md, GEMINI.md (configs for other AI tools)
- agents/ folder scaffold (5 roles: ceo, engineer, product, marketing, tester)
- examples/ (sample session files, progress file)

## Building
- Demo readiness polish

## Blockers
- None

## Key Decisions
- Skills live at .claude/skills/ (not skills/) — correct Claude Code path (commit 98360b4)
- README uses two setup paths (add-to-existing vs fresh start) instead of clone-and-copy — lower friction for non-technical users (commits 5a6f9d7, 21bc8a7)
- Single shared session file per day, each agent writes its own section — one source of truth, no cross-writing

## Last Updated: 2026-04-09
