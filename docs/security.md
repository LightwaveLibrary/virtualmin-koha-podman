# Security review — release candidate

**Not yet approved for public release or production reuse.**

- The original recipe's `web` startup command wrote an installer page containing `DB_PASSWORD` in browser-delivered JavaScript. Remove that behavior; do not rely on obscurity or a temporary URL.
- Use Virtualmin's deployment secret facility for the database password; never commit actual credentials.
- Keep Koha configuration files containing credentials readable only by the intended service account.
- Keep the GitHub repository private until a clean deployment and security review pass.
- Protect HTTPS and the installer route; disable installer access after setup as appropriate.
- Back up and test restore of database and persistent Koha volumes before upgrades.
