# Copilot instructions for patterson-agents/.github

This is the Patterson org's community-health repository: the org profile README
(`profile/README.md`), shared agent instructions, and the reusable `standards-gate.yml`
workflow under `.github/workflows/` that every Patterson repository calls for CI enforcement
of the house standards.

- The org-wide Copilot instruction text lives in `copilot-org-instructions.md` at the repo
  root; it is pasted into organization settings -> Copilot -> Custom instructions. Change
  the file and the settings page together.
- `standards-gate.yml` must stay reusable (`workflow_call`) and self-contained: POSIX sh
  steps, no repository-specific assumptions, no untrusted event interpolation in `run:`
  blocks. Its denylist pattern is assembled from split string halves on purpose — never
  join them into a contiguous literal.
- The top-level `workflows/` directory (claude.yml and friends) is **not** executed by
  GitHub — only `.github/workflows/` is. Do not add new workflows to the top-level
  directory.
- House rules apply here as everywhere: no Python, bun-only package management, Node 24,
  conventional commits, no emoji, no hardcoded secrets.
