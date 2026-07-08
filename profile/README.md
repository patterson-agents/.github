# Patterson Agents

**Enterprise agentic tooling for Patterson Companies.** Shared skills, marketplaces,
policies, and the repos that keep our AI-assisted development trusted, consistent, and
governed across teams.

---

## What lives here

This organization is the single home for the building blocks teams reuse instead of
reinventing:

- **Skills** — packaged, versioned agent skills any team can install. See
  [`patterson-skills`](https://github.com/Patterson-Agents/patterson-skills) for the
  enterprise-wide catalog.
- **Marketplaces** — curated catalogs that make skills, plugins, and agents
  discoverable and installable from a single source.
- **Agentic policies** — the guardrails every automated workflow inherits: supply-chain
  gates, safe-output review, network isolation, and approval flows.
- **Design & brand** — [`design-system`](https://github.com/Patterson-Agents/design-system),
  the brand-accurate Patterson Companies component library and design tokens, published as
  the `patterson-design` skill so agents generate on-brand interfaces by default.

## Built on

We stand on excellent open-source work and mirror a few upstreams here for reference:

- [github/gh-aw](https://github.com/github/gh-aw) — GitHub Agentic Workflows: author
  agent workflows in markdown, compiled to secure, sandboxed GitHub Actions.
- [githubnext/agentics](https://github.com/githubnext/agentics) — GitHub Next's library
  of reusable agentic workflows and patterns.
- [anthropics/skills](https://github.com/anthropics/skills) — Anthropic's open collection
  of agent skills.
- [`ado-aw`](https://github.com/Patterson-Agents/ado-aw) — reference: the Azure DevOps
  analog of gh-aw, compiling markdown workflows into network-isolated ADO pipelines.

## Getting started

1. Browse the repos above for the capability you need.
2. Install skills and plugins from the marketplace rather than copying them — you get
   updates and policy compliance for free.
3. Read a repo's `README.md` / `SKILL.md` before building on it.

## How we work

Every agentic workflow here follows the same trust model: **agents propose, review
gates decide, and only a separate executor writes.** Automation runs with least
privilege, dependencies pass a supply-chain check before they land, and outputs are
scanned for prompt injection and secret leaks before they take effect.

## Resources

**Skills & marketplaces**

- [Awesome Copilot](https://awesome-copilot.github.com/) — community catalog of Copilot
  instructions, prompts, and chat modes.
- [Agent Skills directory](https://agentskills.io) — discover and share agent skills.

**Documentation**

- [Claude docs](https://claude.com/docs) — product docs for Claude and Claude Code.
- [Claude Developer Platform](https://platform.claude.com/docs) — API, Agent SDK, tools,
  and Agent Skills references.
- [Model Context Protocol](https://modelcontextprotocol.io) — the open standard for
  connecting agents to tools and data.
- [GitHub Copilot docs](https://docs.github.com/copilot) — Copilot features, agents, and
  configuration.

---

*Patterson Companies — Trusted Expertise. Unrivaled Support. Since 1877.*
