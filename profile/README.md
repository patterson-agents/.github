<div align="center">

<img src="assets/banner.svg" width="100%" alt="Patterson Agents — AI agent platform for Patterson Companies">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/patterson-logo-white.svg">
  <img src="assets/patterson-logo-navy.svg" alt="Patterson Companies" width="240">
</picture>

# patterson-agents

**Trusted Expertise. Unrivaled Support.** — Patterson's institutional knowledge,
encoded as installable agent capability.

![marketplaces](https://img.shields.io/badge/marketplaces-7-7BFF1B?labelColor=001B34)
![plugins](https://img.shields.io/badge/plugins-15-055ABD?labelColor=001B34)
![skills](https://img.shields.io/badge/plugin_skills-26-0065FF?labelColor=001B34)
![library](https://img.shields.io/badge/vendored_skill_library-339-00A8E1?labelColor=001B34)
![surfaces](https://img.shields.io/badge/surfaces-Claude_·_Copilot_·_VS_Code-00817D?labelColor=001B34)
![provenance](https://img.shields.io/badge/every_assertion-sourced-58585B?labelColor=001B34)

</div>

---

## What this is

Patterson Companies holds a large body of institutional knowledge — engineering standards, brand and editorial rules, architectural conventions, operational practice, and domain expertise particular to dental and veterinary distribution. Most of it lives in documents that people read once and then approximate from memory. The standard exists; the person who needed it never found it. Local practice drifts from documented practice, invisibly. A control gets assumed covered because something adjacent to it exists.

This organization makes that knowledge **available to AI agents at the moment of use** — versioned, attributable, reviewable, and owned by the teams accountable for it. The organizing intent is that an agent working on Patterson code should behave the way a well-oriented Patterson colleague would: aware of the standards that apply, able to cite them, and able to say plainly when a standard does not cover the situation at hand. Every assertion traces to a source you can open. Where a source is silent, the silence is recorded as a gap rather than filled with a plausible invention — an invention quietly becomes policy, while an acknowledged gap prompts someone to go fix it.

> [!NOTE]
> Every repository in this organization is **private**. The links below resolve for org members; if a link 404s for you, you need access rather than a different URL.

### The layered model

Knowledge is not uniform. Some applies to all of Patterson; some only to a business segment, a department, a team, or a single repository. The marketplaces reflect that shape rather than flattening it.

```text
enterprise  ──  patterson-corp              true for all of Patterson
   └─ sub-org  ──  patterson-dental · patterson-vet
        └─ department  ──  plugins within a catalog
             └─ team  ──  groupings and presets
                  └─ repo  ──  .claude/settings.json beside the code
                       └─ user  ──  individual preference
```

Lower layers **extend** what they inherit by default, and **may override** when they know better. Divergence is treated as information about where a parent standard is incomplete — not as a violation to suppress.

---

## Quick start

Add a marketplace, then enable the plugins you want. Inside Claude Code:

```bash
# 1 — register the enterprise catalog
/plugin marketplace add patterson-agents/patterson-corp

# 2 — enable what applies to your work
/plugin install patterson-engineering@patterson-corp
/plugin install patterson-brand@patterson-corp

# 3 — add more catalogs as needed
/plugin marketplace add patterson-agents/design-plugins
/plugin marketplace add patterson-agents/patterson-labs
```

> [!WARNING]
> Marketplace names occupy a **flat global namespace**, and the `@suffix` on an install command is the marketplace's `name` field — *not* its repository name. `patterson-marketplace` publishes under the name `patterson`; `design-plugins` publishes under `patterson-design`. Registering a second catalog under an existing name replaces the first rather than merging with it.

VS Code and GitHub Copilot consume the same catalog — they read the identical `extraKnownMarketplaces` and `enabledPlugins` keys and defer to the same `marketplace.json` schema (see [ADR 0002](https://github.com/patterson-agents/patterson-corp/blob/main/docs/decisions/0002-cross-vendor-manifest-projection.md)).

**Rolling this out for a team or the org?** Settings compose across managed, enterprise, project, and user layers with well-defined precedence — and some of it is winner-take-all rather than merged. Read [`patterson-corp/docs/architecture/layered-settings.md`](https://github.com/patterson-agents/patterson-corp/blob/main/docs/architecture/layered-settings.md) before writing anything into `managed-settings.d`.

---

## Marketplaces

| Catalog | Marketplace `name` | Status | Plugins |
|---|---|---|---|
| [`patterson-corp`](https://github.com/patterson-agents/patterson-corp) | `patterson-corp` | ![governed](https://img.shields.io/badge/governed-7BFF1B?labelColor=001B34) | 2 |
| [`design-plugins`](https://github.com/patterson-agents/design-plugins) | `patterson-design` | ![governed](https://img.shields.io/badge/governed-7BFF1B?labelColor=001B34) | 9 |
| [`patterson-labs`](https://github.com/patterson-agents/patterson-labs) | `patterson-labs` | ![incubating](https://img.shields.io/badge/incubating-00A8E1?labelColor=001B34) | 2 |
| [`patterson-marketplace`](https://github.com/patterson-agents/patterson-marketplace) | `patterson` | ![incubating](https://img.shields.io/badge/incubating-00A8E1?labelColor=001B34) | 1 |
| [`patterson-dental`](https://github.com/patterson-agents/patterson-dental) | `patterson-dental` | ![domain](https://img.shields.io/badge/domain-055ABD?labelColor=001B34) | 0 |
| [`patterson-vet`](https://github.com/patterson-agents/patterson-vet) | `patterson-vet` | ![domain](https://img.shields.io/badge/domain-055ABD?labelColor=001B34) | 0 |
| [`patterson-skills`](https://github.com/patterson-agents/patterson-skills) | `patterson-skills` | ![deprecated](https://img.shields.io/badge/deprecated-58585B?labelColor=001B34) | 1 |

<details>
<summary><b><code>patterson-corp</code></b> — enterprise · 2 plugins · 12 skills&nbsp; <img src="https://img.shields.io/badge/governed-7BFF1B?labelColor=001B34" align="center"></summary>

<br>

Capability true for all of Patterson: the standards layer and the brand layer. This is the catalog every Patterson engineer should have registered.

| Plugin | What it does |
|---|---|
| **`patterson-engineering`** `v0.2.0` | Encodes Patterson's IT standards for CI/CD, Azure environments, compute, storage and data classification, and monitoring — sourced from the ServiceNow IT Standards & Guidelines knowledge base. |
| **`patterson-brand`** `v0.1.0` | Patterson brand identity, design tokens, and editorial voice, with a drop-in Tailwind v4 + shadcn/ui theme derived from the 2025 Brand Guide. |

<details>
<summary><code>patterson-engineering</code> — 7 skills</summary>

- `cicd-pipeline-standards` — pipeline structure, gates, and required controls
- `azure-environment-standards` — environment topology and naming
- `azure-compute-standards` — compute selection and configuration
- `storage-data-standards` — storage choice and data classification
- `monitoring-alerting-standards` — observability and alerting requirements
- `github-security-scanning` — required scanning configuration on GitHub
- `approved-software-check` — is this tool approved for use at Patterson?

</details>

<details>
<summary><code>patterson-brand</code> — 5 skills</summary>

- `brand-identity` — logos, marks, and identity rules
- `design-tokens` — the token set and its framework adapters
- `copy-style-guide` — editorial mechanics and house style
- `voice-and-tone` — voice per sub-brand
- `presentation-templates` — on-brand decks and documents

</details>

```bash
/plugin marketplace add patterson-agents/patterson-corp
/plugin install patterson-engineering@patterson-corp
/plugin install patterson-brand@patterson-corp
```

</details>

<details>
<summary><b><code>design-plugins</code></b> — design system · 9 plugins · marketplace name <code>patterson-design</code>&nbsp; <img src="https://img.shields.io/badge/governed-7BFF1B?labelColor=001B34" align="center"></summary>

<br>

The Patterson design system packaged as nine individually installable plugins. Each ships a skill, slash commands, a subagent, and a self-contained `ds/` design-system snapshot — no build step, no CDN. **Install `patterson-brand` first**; the rest build on it.

| Plugin | What it is | Skill |
|---|---|---|
| **`patterson-brand`** `v1.1.0` | Design-system core — tokens, fonts, logos, brand imagery, React components, guideline specimens, and framework adapters (Tailwind v3/v4, UnoCSS, Theme UI, shadcn/ui) | `patterson-design` |
| **`patterson-deck`** `v1.1.0` | 16:9 presentation template — cover, section dividers, stats, comparison, quote, capabilities table, photo band, closing | `deck-template` |
| **`patterson-executive-deck`** `v1.1.0` | Executive briefing deck — navy cover, key takeaways, breakdown matrix, requirements, outputs, benefits | `executive-deck-template` |
| **`patterson-corporate-page`** `v1.1.0` | Corporate web page shell — sticky nav, navy hero, content band, footer | `corporate-page-template` |
| **`patterson-corporate-website`** `v1.1.0` | Corporate-site UI kit — recreation of pattersoncompanies.com as separate React screens | `corporate-website-kit` |
| **`patterson-storefront`** `v1.1.0` | E-commerce storefront kit (pattern library v5.7.2 shell) with a Dental ↔ Veterinary brand toggle | `storefront-kit` |
| **`patterson-file-manager`** `v1.1.0` | "Skill Studio" application shell — top bar, sidebar tree, content grid; a template for internal tools | `file-manager-template` |
| **`patterson-docs`** `v1.1.0` | Documentation-site package — VitePress + Diátaxis UI kit and a browser-openable page template | `docs-site` |
| **`patterson-tutorialkit`** `v1.3.0` | Astro TutorialKit theme — runnable starter, canonical `theme.css`, and a 5-part / 18-lesson agent-tooling curriculum | `tutorialkit-theme` |

```bash
/plugin marketplace add patterson-agents/design-plugins
/plugin install patterson-brand@patterson-design
/plugin install patterson-deck@patterson-design
```

> [!IMPORTANT]
> Two plugins named `patterson-brand` exist — one here (`@patterson-design`, the design-system core) and one in `patterson-corp` (`@patterson-corp`, the brand-standards encoding). The collision is at the plugin tier, not the marketplace tier; see [ADR 0003](https://github.com/patterson-agents/patterson-corp/blob/main/docs/decisions/0003-plugin-name-reconciliation.md). Always qualify installs with the `@marketplace` suffix.

</details>

<details>
<summary><b><code>patterson-labs</code></b> — incubation · 2 plugins · 3 skills&nbsp; <img src="https://img.shields.io/badge/incubating-00A8E1?labelColor=001B34" align="center"></summary>

<br>

Where experimental capability earns its way into `patterson-corp`. Nothing here is enterprise policy yet.

| Plugin | What it is | Skills |
|---|---|---|
| **`patterson-workflows`** `v0.1.0` | A conversational interview that designs one complete GitHub Agentic Workflow (`gh aw`) file from a stated goal — trigger, scope, data strategy, guardrails, network, engine | `agentic-workflow-designer` |
| **`patterson-design-imports`** `v0.1.0` | Design tokens imported from the Patterson Academy and lab-workshop authoring projects. Each ships a Tailwind v4 `theme.css`, a W3C `tokens.json`, a byte-identical generator, and a drift check — with every conflict against the 2025 Brand Guide recorded and the Brand Guide winning | `academy-design-tokens` · `lab-workshop-design-tokens` |

```bash
/plugin marketplace add patterson-agents/patterson-labs
/plugin install patterson-workflows@patterson-labs
```

> [!NOTE]
> `patterson-design-imports` does **not** supersede `patterson-brand`. That supersession ruling is still open.

</details>

<details>
<summary><b><code>patterson-marketplace</code></b> — org catalog + vendored skill library · 1 plugin · marketplace name <code>patterson</code>&nbsp; <img src="https://img.shields.io/badge/incubating-00A8E1?labelColor=001B34" align="center"></summary>

<br>

| Plugin | What it is | Skill |
|---|---|---|
| **`patterson-design`** | The Patterson design system as a single plugin: brand tokens, components, voice, and logos for on-brand interfaces, prototypes, and slides | `patterson-design` |

The repo also ships a `_template/` plugin scaffold, plugin-management scripts (`scripts/plugins.sh add|update|remove`), a curated internal docs library, and `docs/managed-settings.template.json` for org rollout.

**Also here: a vendored skill library of ~339 skill directories** under `.agents/skills/`. It is a *library* — a working reference collection of third-party and internal skills — **not a published marketplace**, and nothing in it is Patterson policy.

```bash
/plugin marketplace add patterson-agents/patterson-marketplace
/plugin install patterson-design@patterson
```

</details>

<details>
<summary><b><code>patterson-dental</code></b> and <b><code>patterson-vet</code></b> — sub-org domain catalogs · 0 plugins&nbsp; <img src="https://img.shields.io/badge/domain-055ABD?labelColor=001B34" align="center"></summary>

<br>

Both catalogs are **structurally complete and awaiting domain skills**. They exist now so that segment-particular capability has an obvious home the moment someone writes it — rather than being flattened into the enterprise catalog because there was nowhere else to put it.

The organization spans business segments with genuinely different customers, vocabulary, and practice. Those differences are real and should not be collapsed into a false common case.

| Catalog | Scope | Repo |
|---|---|---|
| `patterson-dental` | Capability specific to Patterson's dental distribution business | [patterson-agents/patterson-dental](https://github.com/patterson-agents/patterson-dental) |
| `patterson-vet` | Capability specific to Patterson's veterinary distribution business | [patterson-agents/patterson-vet](https://github.com/patterson-agents/patterson-vet) |

```bash
/plugin marketplace add patterson-agents/patterson-dental
/plugin marketplace add patterson-agents/patterson-vet
```

</details>

<details>
<summary><b><code>patterson-skills</code></b> — deprecated&nbsp; <img src="https://img.shields.io/badge/deprecated-58585B?labelColor=001B34" align="center"></summary>

<br>

The earliest Patterson marketplace, carrying a single `patterson-design` plugin. **Superseded** — its manifest says so explicitly. Use [`design-plugins`](https://github.com/patterson-agents/design-plugins) for the design system and [`patterson-corp`](https://github.com/patterson-agents/patterson-corp) for brand standards. Repo: [patterson-agents/patterson-skills](https://github.com/patterson-agents/patterson-skills).

</details>

---

## Platform repositories

<details>
<summary><b>Six repos that build, document, and teach the platform</b></summary>

<br>

| Repo | What it is |
|---|---|
| [**`cli`**](https://github.com/patterson-agents/cli) | `patterson` — a template-driven scaffolder *and* a standing configuration manager for AI-assisted development. Instructions live in four incompatible files across Claude, Copilot, VS Code, and Zed; MCP servers in four more. `patterson.config.ts` is one canonical model that compiles to every surface, then keeps watching so hand edits are never lost and drift is always reported. Bun workspaces monorepo. |
| [**`patterson-platform-docs`**](https://github.com/patterson-agents/patterson-platform-docs) | The reference library behind the platform — vendor documentation, open specifications, and assessments captured with a source URL, a capture date, and a completeness note, so a decision can be checked against what was actually true when it was made. A library, not an authority. |
| [**`patterson-design-system`**](https://github.com/patterson-agents/patterson-design-system) | The claude.ai/design **authoring project** for the design system — tokens, components, guidelines, integrations, templates. Not the canonical published system; it has materially diverged from `design-plugins`, and which supersedes which is an open decision. |
| [**`patterson-academy`**](https://github.com/patterson-agents/patterson-academy) | Claude Code Academy — a self-contained static training deck covering AGENTS.md, commands, skills, plugins, MCP, hooks, and sandboxing. No build required. |
| [**`lab-workshop`**](https://github.com/patterson-agents/lab-workshop) | TechDays: AI Fluency — Agentic Agents. A half-day hands-on lab: a 35-slide deck plus a TutorialKit course of 5 parts / 18 lessons. No build required. |
| [**`patterson-sh`**](https://github.com/patterson-agents/patterson-sh) | The `patterson.sh` workspace shell — meta-tooling home for the platform. Scaffolding, not a shipping product. |

</details>

---

## Governance

Decisions that shape the platform are written down as ADRs, with the decider and the date on the record. Where a decision depends on an approval Patterson has not yet given, it is marked **provisional** rather than presented as settled.

| ADR | Decision | Status |
|---|---|---|
| [0001](https://github.com/patterson-agents/patterson-corp/blob/main/docs/decisions/0001-spec-framework.md) | OpenSpec is the spec-driven framework for org-level planning | Accepted — **provisional** on Approved Software review |
| [0002](https://github.com/patterson-agents/patterson-corp/blob/main/docs/decisions/0002-cross-vendor-manifest-projection.md) | The Copilot/VS Code manifest is a *copy* of `marketplace.json`, not a transformation | Accepted |
| [0003](https://github.com/patterson-agents/patterson-corp/blob/main/docs/decisions/0003-plugin-name-reconciliation.md) | The `patterson-brand` name collision is at the plugin tier, not the marketplace tier | Accepted in part; `patterson-brand` section still Proposed |
| [0004](https://github.com/patterson-agents/design-plugins/blob/main/docs/decisions/0004-unpkg-react-application-templates.md) | React-via-unpkg application templates in `patterson-docs` and `patterson-file-manager` | Proposed |

### The promotion path

Work begins in [`patterson-labs`](https://github.com/patterson-agents/patterson-labs) and graduates to [`patterson-corp`](https://github.com/patterson-agents/patterson-corp) against a **written gate** — tests green, provenance complete, and the other criteria in [`patterson-labs/docs/promotion-path.md`](https://github.com/patterson-agents/patterson-labs/blob/main/docs/promotion-path.md). The gate was written before anything went through it, so "promote it" is not a judgment call made differently each time.

### Provenance rules

Every skill carries **`_SOURCES.md`** (where its knowledge came from, with a confidence rating) and **`REFERENCES.md`** (canonical locations a reader can open). An agent restating a standard is indistinguishable — to the reader — from an agent inventing one, so the distinction has to be structural rather than stylistic.

> [!IMPORTANT]
> This platform never manufactures organizational policy. Where a source is genuinely silent, you will find a **`[TBD]`** marker: a recorded gap, deliberately left unfilled. When encoded knowledge appears to require something Patterson has not actually stated, that is a finding to escalate — not a decision to make here.

### Contributing

Ownership follows accountability: the group responsible for a body of knowledge owns its encoding. Contribution paths exist at every layer, and local divergence is treated as a signal about the parent standard rather than a violation. Open an issue on the relevant repository, or start in `patterson-labs`.

---

<div align="center">

<img src="assets/techdays-fy27-mark.png" alt="TechDays FY27" width="120">

**Connect. Create. Charge.**

<sub>Patterson logos, brand imagery, and Proxima Nova are proprietary. Internal distribution only.<br>
© Patterson Companies</sub>

</div>
