# NEXORA build notes
Original UI prototype with local browser demo features and privacy-first backend schema.

## Currently in repo
- Home feed, stories UI, Explore, Reels placeholder, profile edit, post media/caption, likes, comments, saved posts, local-only chat screen, notifications placeholder.
- Demo posts/messages are stored in this browser's local storage only; they are not synced and do not reach other users.
- PWA manifest/offline shell and GitHub Actions Android debug APK workflow.

## Backend activation (not yet connected to app)
1. Create a Supabase project.
2. SQL Editor: run `supabase/schema.sql`.
3. Configure private media bucket/policies (included in SQL).
4. Set Supabase URL + anon/public key in config.js. NEVER place service-role keys or secrets in client code.
5. Authentication provider must be enabled and email verification configured.
6. Review and test RLS policies before public launch. Current SQL is a starting point, not a security audit. Public feed/private-account policies need tightening before private accounts are launched; call signaling needs a trusted server and TURN configuration.

## Android APK
GitHub Actions -> Actions -> Build NEXORA Android APK. Trigger a workflow manually or by pushing to main. Download APK from workflow artifacts when run completes. APK is a debug build, not Play Store signing.

## Not implemented yet
Actual multi-user backend connectivity, authentication UI/provider integration, secure server-side feed visibility, real DMs, end-to-end encryption, real WebRTC calls, moderation/reporting pipeline, and production-grade private media signed-url access. The current browser chat is not delivered to other people.
