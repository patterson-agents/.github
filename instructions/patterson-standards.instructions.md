---
applyTo: "**"
---

# Patterson house standards

These rules are organization policy, enforced by CI (`standards-gate.yml`), Claude Code
hooks, and managed settings. Follow them in every suggestion and generated change.

- No Python: no `.py` files, no `python`/`pip`/`pipx`/`uv`/`poetry`/`conda` commands. Use
  zero-dependency TypeScript (`bun run script.ts` / `node script.ts`) or Nushell.
- bun is the only package manager: never `npm`/`pnpm`/`yarn`/`npx`, never create or update
  `package-lock.json`, `npm-shrinkwrap.json`, `yarn.lock`, or `pnpm-lock.yaml`.
- Score every new or upgraded dependency with the Socket CLI
  (`socket package shallow npm <pkg> --markdown`) and surface any dimension under 90 before
  installing. Never reference the June 2026 AUR-attack packages (`atomic-lockfile`,
  `js-digest`, `lockfile-js`, `nextfile-js`) or anything published by `herbsobering`.
- No hardcoded secrets; reference a secrets manager at runtime.
- Node 24 family only for pinned runtimes and images.
- Conventional commits: `<type>(<scope>): <summary>`.
- No emoji in shipped content; use GFM alerts and tables.
