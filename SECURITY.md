# Security Policy

## Report privately

Do not disclose a suspected vulnerability in a public issue, discussion, pull request, commit message, or deployment log.

Use GitHub's private vulnerability-reporting flow when available:

https://github.com/sourbehnam1374-beep/run-001/security/advisories/new

If that route is unavailable, contact the maintainer through an established private channel.

## Sensitive material

Never commit or deploy:

- credentials, tokens, private keys, webhook URLs, wallet addresses, or signed integration URLs;
- buyer or participant identities, payment records, private messages, email addresses, or validation screenshots;
- patient information, clinical images, DICOM files, EHR/PACS exports, or re-identifiable clinical records;
- `.env` contents, Cloudflare credentials, or private analytics exports.

Use synthetic, public, or explicitly redistributable examples only.

## Deployment boundary

Cloudflare must serve assets only from `site/`. Do not change `wrangler.jsonc` to expose the repository root. Treat any route that returns repository documentation, state, logs, or validation records as a security defect.

If sensitive material is exposed, stop sharing, rotate affected credentials, remove the current copy, and assess Git history, deployment caches, artifacts, and forks. Deleting a file in a later commit does not remove earlier copies.
