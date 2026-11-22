# NEXORA build notes
Original UI prototype with local browser demo features and privacy-first backend schema.

## Currently in repo
- Home feed, stories UI, Explore, Reels placeholder, profile edit, post media/caption, likes, comments, saved posts, local-only chat screen, notifications placeholder.
- Demo posts/messages are stored in this browser's local storage only; they are not synced and do not reach other users.
- PWA manifest/offline shell and GitHub Actions Android debug APK workflow.

## Backend activation (auth UI is in the app; cloud features still need configuration)\n1. Create a Supabase project at https://supabase.com and copy the Project URL and anon/public key.\n2. Open config.js and paste those two public values. Never use the service-role key in client code.\n3. In Supabase Authentication settings, enable email/password and set site URL/redirect URLs to your published app URL.\n4. SQL Editor: run supabase/schema.sql. The signup profile trigger creates the profile after registration.\n\n## Backend activation (remaining cloud features)
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
