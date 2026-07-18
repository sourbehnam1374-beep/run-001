# Contributing to the SHIVA Design System

Keep pull requests focused and include a short before/after description.

## Design requirements

- Use the existing tokens and semantic color families.
- Keep artifacts usable without external fonts, scripts, CDNs, or network calls.
- Preserve keyboard access, selectable text, print legibility, and `prefers-reduced-motion`.
- Add both dark and light behavior where the component uses color.
- Use motion only when it encodes state or process.
- Describe the meaning of each visual change in the pull request.

## Public-data boundary

Use synthetic or clearly public and redistributable examples. Do not commit patient information, buyer identities, payment records, private messages, credentials, wallet addresses, live integration URLs, or private validation artifacts.

## Deployment boundary

Only files under `site/` are deployable. Do not point Wrangler at the repository root. Verify that repository files such as `README.md` and development logs return 404 from the deployed host.

Report security issues using [SECURITY.md](SECURITY.md).
