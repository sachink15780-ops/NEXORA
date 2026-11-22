# Security status

This repo currently contains only a front-end prototype. Production authentication, server authorization, private cloud media, secure messaging, and calling are not implemented.


## Rules before production
- Secrets must stay out of the repo and client bundle. Use server-side secret storage.
- Database tables must have deny-by-default Row-Level Security and tested ownership/participant policies.
- Private media must be in private storage; authorize every access and use expiring signed URLs as appropriate.
- Admin uses least privilege and MFA; admin cannot view user passwords.
- Message end-to-end encryption requires a vetted protocol and independent review before claiming it.
- Validate file types/sizes server-side; rate-limit auth, upload and messaging actions.
- Add account deletion, backups, audit logging, abuse reporting, and security tests.

No app can guarantee zero data leakage. Security claims should match verified implementation.