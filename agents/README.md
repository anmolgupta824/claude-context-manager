# Agents (Optional)

This folder is optional. Delete it if you're using single-agent mode.

If you keep it, each agent has a HEARTBEAT.md that tracks their current status. The /wrap-up skill updates the relevant agent's HEARTBEAT.md at end of session.

## Roles

| Agent | Role | Access |
|-------|------|--------|
| CEO | Strategic oversight, final calls | Everything |
| Engineer | Build, fix, deploy | Code only. No marketing. |
| Product | Strategy, specs, roadmap | Product docs only. No code. |
| Marketing | Content, brand, growth | Marketing only. No code or product docs. |
| Tester | QA, testing, bugs | Read code. Write reports. No code edits. |

## No Agent Selected?

If you run /wrap-up without selecting an agent, it falls back to CEO mode. CEO has full access and sees everything. That's the natural default.

## Want Full Agent Personalities?

For complete soul files, identity files, and detailed agent configurations, see [ai-native-agents](https://github.com/anmolgupta824/ai-native-agents).

This repo keeps agents lightweight. Just HEARTBEAT.md for context persistence. The ai-native-agents repo has the full personality system.
