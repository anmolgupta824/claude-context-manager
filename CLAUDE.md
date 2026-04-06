# CLAUDE.md

## Project Context Loading
On startup, read these files in this order:
1. PROGRESS.md — big picture project status
2. Latest file in docs/sessions/ — yesterday's detailed context
3. If agents/ folder exists and a role is assigned, read that agent's HEARTBEAT.md

Do NOT read all session files. Only the most recent one.
Do NOT read other agents' files unless you are the CEO agent.

## Skills
- /wrap-up — End of day. Creates session file, updates PROGRESS.md, writes agent status.

## Context Management Rules
- Run /clear between unrelated tasks
- Run /compact with a focus message at 60% context usage (don't wait for auto-compact at 83%)
- Use /btw for side questions that shouldn't enter main context
- Commit code before running /clear

## Agent System (Optional)
If agents/ folder exists, this project uses a multi-agent setup.
Each agent has: SOUL.md (how it thinks), IDENTITY.md (who it is), HEARTBEAT.md (current status).
Agents stay in their lane. Engineer can't touch marketing. Product can't write code. Tester reads code but can't edit.
If no agent is selected, default to CEO mode (full access).

See agents/ folder for role definitions.

## Session Files
- One file per day in docs/sessions/
- Format: YYYY-MM-DD-session.md
- Each agent writes their own section
- Single-agent mode: one Summary section
