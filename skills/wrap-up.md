# /wrap-up Skill

## Description
End of session routine. Creates a daily session file, updates progress, and writes agent status.

## Instructions

When the user runs /wrap-up, do the following:

### Step 1: Determine Mode
- Check if agents/ folder exists in the project
- Check if a specific agent role was assigned during this session
- If agent assigned: write that agent's section
- If no agent assigned but agents/ folder exists: fall back to CEO mode, write CEO section
- If no agents/ folder: write a single Summary section

### Step 2: Create or Append to Session File
- File path: docs/sessions/YYYY-MM-DD-session.md (use today's date)
- If the file already exists (multiple wrap-ups in one day), append to it
- If it doesn't exist, create it with the date header

### Step 3: Write Session Content

**Single agent mode (no agents/ folder):**
```markdown
# Session: YYYY-MM-DD

## Summary
- [What was worked on today]
- [Decisions made and why]
- [What was deployed/shipped]
- [Blockers if any]
- [What to do tomorrow]
```

**Multi-agent mode (agents/ folder exists):**
Write only the current agent's section using this format:
```markdown
## [Agent Name]
- [What this agent did today]
- [Decisions made]
- [Status of ongoing work]
- [Blockers]
- [What's next]
```

If this is CEO mode (no agent selected), also add a Blockers (Cross-Team) section at the end.

### Step 4: Update PROGRESS.md
- Read current PROGRESS.md
- Update status, live items, building items, blockers, and date if anything changed
- If nothing changed, leave it as is

### Step 5: Update HEARTBEAT.md (Multi-Agent Only)
- If running in agent mode, update the current agent's HEARTBEAT.md with:
  - Last Updated date
  - Currently working on
  - Blocked on
  - Next session priorities

### Step 6: Output Summary
- Print a clean summary to the terminal showing what was logged
- If multi-agent, show which agent's section was written
- Confirm session file path and PROGRESS.md status
