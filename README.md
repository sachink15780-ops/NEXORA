# NEXORA

Original mobile-first social media app, developed with privacy-by-design principles.

## Stage 1 — UI foundation
Responsive shell, stories row, feed mockups, like interaction, gallery photo/video picker with preview, and local-session post UI.

**Prototype only:** This version is not connected to a backend. It does not create accounts, upload posts to a server, or expose selected media to other people. Avoid real personal data.

## Planned backend
- Managed authentication; no app-side plaintext password storage
- PostgreSQL with deny-by-default Row-Level Security (RLS)
- Private media storage with authorization checks and signed URLs
- Messages scoped to verified chat participants; end-to-end encryption only after vetted protocol implementation and tests
- WebRTC calls with authenticated signaling
- Rate limits, report/block, admin least-privilege, security tests and account deletion

## Security
Never commit API keys, service-role secrets, private keys, tokens, credentials, or real user data. Frontend-only checks are not authorization. See SECURITY.md.


## Run
Open index.html in a browser or deploy static files.