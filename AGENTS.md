# AGENTS.md — Multi-Platform Context Manager Configuration
# Works with: Cursor, Copilot, Windsurf, Codex, Devin, Replit

## Context Loading
On startup, read these files in order:
1. PROGRESS.md — big picture project status
2. Latest file in docs/sessions/ — yesterday's detailed context
3. If a role is assigned, read that agent's HEARTBEAT.md from agents/

Only read the most recent session file. Not all of them.

## End of Session
When asked to wrap up:
1. Create or append to today's file: docs/sessions/YYYY-MM-DD-session.md
2. Write your section (or a single Summary section if no agents)
3. Update PROGRESS.md if project status changed
4. Update your HEARTBEAT.md if using agents

## Agent Roles (Optional)
If agents/ folder exists:
- CEO — full access, strategic decisions, default role
- Engineer — code, builds, deploys. Cannot touch marketing.
- Product — specs, roadmap, priorities. Cannot write code.
- Marketing — content, growth. Cannot touch code or product docs.
- Tester — QA, bugs. Can read code, cannot edit.

## Context Management
- Clear context between unrelated tasks
- Compact with guidance at 60% usage
- Commit code before clearing context
