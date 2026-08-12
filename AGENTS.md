# AGENTS.md

This is `patterson-agents/.github`: the org's community-health repository. It carries the org
profile README (`profile/README.md`), shared skills and agent docs, and the **reusable
standards gate** at `.github/workflows/standards-gate.yml` that enforces Patterson house
standards in CI for every repository that calls it.

## House standards (org-wide, hard-enforced)

CI (`standards-gate.yml`) and Claude Code hooks (`patterson-engineering@patterson-corp`
plugin) block violations of these; do not attempt them:

- **No Python.** No `.py` files, no `python`/`pip`/`uv`/`poetry`/`conda` commands. Use
  zero-dependency TypeScript (`bun run script.ts`) or Nushell.
- **bun only.** Never `npm`/`pnpm`/`yarn`/`npx`; never write a foreign lockfile. `bun.lock`
  is the only lockfile.
- **Supply-chain denylist.** The four June 2026 AUR-attack npm packages and their publisher
  are blocked everywhere; score new dependencies with the Socket CLI before adding.
- **No hardcoded secrets.** Secrets managers only.
- **Node 24**, **conventional commits**, **no emoji** in shipped content.

The full model and activation runbook:
`patterson-agents/patterson-corp` -> `docs/architecture/org-enforcement.md`.

## Repository quirks

- Only `.github/workflows/` executes. The top-level `workflows/` directory is inert
  reference material; do not add workflows there.
- `copilot-org-instructions.md` is the canonical org-wide Copilot instruction text; it must
  be pasted into organization settings -> Copilot -> Custom instructions whenever it
  changes (GitHub does not read it from this repository).
- `profile/README.md` is the public org profile; `README.md` symlinks to it.
