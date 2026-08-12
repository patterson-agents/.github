# Patterson organization instructions for GitHub Copilot

> [!IMPORTANT]
> GitHub reads organization-wide Copilot instructions from **organization settings ->
> Copilot -> Custom instructions**, not from this repository. This file is the canonical
> source of that text: paste the section below into the settings page verbatim, and update
> both together. Repo-level `.github/copilot-instructions.md` files add repo detail on top;
> personal > repository > organization is Copilot's precedence order.

## Paste everything below this line

You are working in a Patterson Companies repository. These rules are organization policy and
are enforced by CI (the `standards-gate` workflow) and by in-session hooks for Claude Code;
follow them in every suggestion, review, and generated change.

- **No Python.** Do not write `.py` files or suggest `python`, `pip`, `pipx`, `uv`,
  `poetry`, or `conda` commands. Implement scripts in zero-dependency TypeScript (run with
  `bun run script.ts` or `node script.ts`) or Nushell.
- **bun is the only package manager.** Use `bun install`, `bun add`, and `bunx`. Never
  suggest `npm`, `pnpm`, `yarn`, or `npx`; never create or update `package-lock.json`,
  `npm-shrinkwrap.json`, `yarn.lock`, or `pnpm-lock.yaml`. `bun.lock` is the only lockfile,
  and a foreign lockfile in a repository is a bug to remove.
- **Supply-chain gate.** Before adding or upgrading any dependency, it must be scored with
  the Socket CLI (`socket package shallow npm <pkg> --markdown`); any dimension under 90 is
  flagged to a human before install. Never reference the June 2026 AUR-attack packages
  (`atomic-lockfile`, `js-digest`, `lockfile-js`, `nextfile-js`) or anything published by
  `herbsobering`.
- **No hardcoded secrets.** Reference secrets from a secrets manager at runtime; never place
  keys, tokens, or connection strings with embedded passwords in code, config, or CI files.
- **Node 24.** Pin `node:24`-family images and runtimes; never introduce an older Node pin.
- **Conventional commits.** `<type>(<scope>): <summary>` with `feat`, `fix`, `docs`, `test`,
  `chore`, `refactor`.
- **No emoji in shipped content.** Patterson is a B2B healthcare distribution brand; use GFM
  alerts and tables for emphasis.
- **Brand and engineering standards live in `patterson-agents/patterson-corp`** as
  installable plugins (`patterson-engineering`, `patterson-brand`). When a repository has its
  own `copilot-instructions.md` or `AGENTS.md`, those take precedence over this text.
