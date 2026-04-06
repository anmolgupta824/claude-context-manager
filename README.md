# Claude Context Manager

Never re-explain your project again. Save daily context, restore it instantly.

Works with Claude Code, Cursor, Copilot, Windsurf, Gemini CLI, Codex, Devin, and Replit.

## The Problem

Every time you start a new Claude Code session, it has zero memory of what you did yesterday. You waste 10 minutes re-explaining your project. Decisions you already made? Gone. Bugs you already found? Forgotten. Context you carefully built up over hours? Wiped clean.

This repo fixes that with 3 files and 1 skill.

## How It Works

```
End of day:
1. Run /wrap-up
2. Claude writes today's session file with everything that happened
3. PROGRESS.md updates with the big picture

Next morning:
1. Open Claude Code
2. CLAUDE.md automatically loads yesterday's session + PROGRESS.md
3. Claude picks up exactly where you left off
```

Total startup context: ~3,000 tokens out of 200,000 available. Clean and lean.

## File Structure

```
claude-context-manager/
├── CLAUDE.md                    ← startup config (reads context automatically)
├── AGENTS.md                   ← config for Cursor, Copilot, Windsurf, etc.
├── GEMINI.md                   ← config for Gemini CLI
├── PROGRESS.md                 ← big picture status (~100 tokens)
├── docs/
│   └── sessions/               ← one file per day, auto-generated
│       ├── 2026-04-01-session.md
│       ├── 2026-04-02-session.md
│       └── ...
├── agents/                     ← optional, for multi-agent setups
│   ├── ceo/
│   ├── engineer/
│   ├── product/
│   ├── marketing/
│   └── tester/
├── skills/
│   └── wrap-up.md              ← /wrap-up skill definition
├── examples/
│   ├── session-file-example.md
│   └── progress-example.md
└── LICENSE
```

## Quick Start (Single Agent)

```bash
# Clone the repo
git clone https://github.com/anmolgupta824/claude-context-manager.git

# Copy into your project
cp CLAUDE.md your-project/CLAUDE.md
cp PROGRESS.md your-project/PROGRESS.md
cp -r skills/ your-project/.claude/skills/
mkdir -p your-project/docs/sessions/

# Start working. At end of day:
# Type /wrap-up in Claude Code
# Tomorrow everything loads automatically
```

## Quick Start (Multi-Agent)

```bash
# Clone the repo
git clone https://github.com/anmolgupta824/claude-context-manager.git

# Copy everything into your project
cp CLAUDE.md your-project/CLAUDE.md
cp PROGRESS.md your-project/PROGRESS.md
cp -r skills/ your-project/.claude/skills/
cp -r agents/ your-project/.claude/agents/
mkdir -p your-project/docs/sessions/

# Open 5 terminals. In each one, tell Claude which agent to load.
# At end of day, run /wrap-up from any terminal.
# Each agent writes their own section in the session file.
```

## How /wrap-up Works

When you run /wrap-up, Claude:

1. Creates (or appends to) today's session file: `docs/sessions/YYYY-MM-DD-session.md`
2. If an agent is selected: writes that agent's section
3. If no agent is selected but agents/ folder exists: falls back to CEO mode (full access, writes CEO section)
4. If no agents/ folder: writes a single summary section
5. Updates PROGRESS.md with any changes to project status
6. Outputs a summary to the terminal

## Session File Format

Each daily session file looks like this:

**Single agent mode:**
```markdown
# Session: 2026-04-05

## Summary
- Built user authentication flow
- Decision: JWT over sessions (sessions required sticky routing, JWT is stateless)
- Deployed to production, all tests passing
- Blocker: None
- Tomorrow: Add password reset flow
```

**Multi-agent mode:**
```markdown
# Session: 2026-04-05

## CEO
- Reviewed all agent status
- Decision: Prioritize digest over interview simulator
- Next: Review engineer's bug fixes tomorrow

## Engineer
- Shipped: Newsletter batch send fix
- Open bugs: BUG-002 (skeleton animation), BUG-003 (RLS policy)
- Deployed: Production, all tests passing
- Next: Fix BUG-002

## Product
- Updated Q2 roadmap
- P0: AI-Native Digest (live)
- P1: Interview Simulator (spec in progress)

## Marketing
- Posted multi-agent thread on Threads
- Next: Sunday evening post planned

## Tester
- Tested newsletter batch send: PASS
- BUG-002 still open (low priority)
- BUG-001 closed: cannot reproduce

## Blockers (Cross-Team)
- None
```

## PROGRESS.md Format

This is your big picture file. Under 200 tokens. Claude reads it on every startup.

```markdown
# Progress

## Status: 99% complete

## Live
- Website, Course, Resume Kit, Job Board, Digest

## Building
- Interview Simulator

## Blockers
- None

## Key Decisions
- Builder-first strategy: repos > LinkedIn posts
- One post per week on LinkedIn

## Last Updated: 2026-04-05
```

## Best Practices

### The 60% Rule
Don't let context exceed 60% capacity. Auto-compaction fires at ~83% and is lossy, keeping only 20-30% of details. Run `/compact` manually with guidance before it gets forced.

### /clear Between Tasks
Finished a feature? Run `/clear` before starting the next one. Context from task A actively hurts task B. Your code is safe in git. Power users /clear 5-10 times per day.

### Guided /compact
Don't just run `/compact`. Tell it what to keep: `/compact Focus on the authentication implementation`. Raw /compact loses important details randomly.

### /btw for Side Questions
Need to ask something unrelated? Use `/btw` instead of typing it in your main session. It spawns a separate sub-request. Main session stays clean. Zero token cost.

### Keep CLAUDE.md Under 2,500 Tokens
Boris Cherny (Claude Code creator) keeps his at ~2,500 tokens. Every token in CLAUDE.md is spent on every session startup. If removing a line wouldn't cause Claude to make mistakes, cut it.

### Commit Often
Commit code frequently so that `/clear` is always safe. If your work is in git, clearing context costs nothing.

### Decisions Log
Record not just what you decided but WHY. Format: "Decision: JWT over sessions. Reason: Sessions required sticky routing. Rejected: OAuth (too complex for MVP)." Six months from now Claude can explain your own architecture to you.

## Multi-Agent Details

Each agent writes ONLY to their own files. No cross-writing.

| Agent | Writes To | Reads |
|-------|-----------|-------|
| CEO | Everything | Everything |
| Engineer | engineer/, code files | engineer/, shared-context/ |
| Product | product/ | product/, shared-context/ |
| Marketing | marketing/ | marketing/, shared-context/ |
| Tester | tester/, test reports | tester/, code files (read only), shared-context/ |

The session file is the ONE shared file where all agents write, but each in their own section.

For the full multi-agent system with soul files, identity files, and heartbeat files, see [ai-native-agents](https://github.com/anmolgupta824/ai-native-agents).

## Learn More

This is the system I use to run [The AI-Native PM](https://theainativepm.com). It saves me 10 minutes every morning. Clone it if you want.

Full Claude Code course: [theainativepm.com/modules](https://theainativepm.com/modules)

## License

MIT
