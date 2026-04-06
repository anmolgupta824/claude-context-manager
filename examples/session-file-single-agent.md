# Session: 2026-04-05

## Summary
- Built user authentication flow with JWT
- Decision: JWT over sessions. Reason: Sessions required sticky routing in Railway deployment which complicated horizontal scaling. JWT is stateless. Rejected: OAuth-only (too complex for MVP).
- Deployed to production. All tests passing (47/47).
- Fixed bug where login redirect failed on mobile Safari
- Blocker: None
- Tomorrow: Add password reset flow, then start on user profile page
