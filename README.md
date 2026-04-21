# OpenAIRT-300

![logo](/openairt-300-lockup-dark.svg)

**An open-source, JavaScript-first alternative to OffSec AI-300.**
Community-buildable, fully hands-on curriculum for offensive AI security.

[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-sa/4.0/)
[![Code: MIT](https://img.shields.io/badge/Code-MIT-blue.svg)](#license)
[![Status: Announcement](https://img.shields.io/badge/Status-Announcement-orange.svg)](#project-status)
[![Community: EU-ACC](https://img.shields.io/badge/Community-eu--acc.ro-purple.svg)](https://eu-acc.ro)

---

## What this is

OpenAIRT-300 is a free, open-source curriculum for training AI red teamers — the engineers who attack LLM-powered applications, agentic systems, RAG pipelines, MCP servers, and the infrastructure around them.

It is designed as an alternative to OffSec's **AI-300 (OSAI+)**, launched March 31, 2026 at $1,749 for a 90-day bundle. OpenAIRT-300 aims at the same depth (~81 hours of instruction + a 24-hour practical exam) with four main differences:

- **Free and open.** CC-BY-SA 4.0 for written content, MIT / Apache-2.0 for lab code. No paywall, no proprietary VPN labs, no vendor lock-in.
- **JavaScript / TypeScript first.** The default stack is Next.js, Vercel AI SDK, LangChain.js, Mastra, Genkit, LangGraph.js, and the TypeScript MCP SDK — because that's where most agentic products actually ship. Python tools are used as sidecars only when there's no JS equivalent.
- **Anchored in real incidents.** Every module is built around a named, published incident from the last 18 months — including the **Vercel × Context.ai** breach (April 19, 2026), which opens the curriculum and runs through it as the spine case study.
- **Mechanism then scale.** Every lab is executed twice: once by hand to build mechanistic understanding, and once wrapped in `promptfooconfig.yaml` with plugin/strategy sweeps and CI wiring. A scan without a working manual exploit behind it is failing work; a manual exploit without CI coverage never survives production drift.

> The goal is to produce practitioners who can walk into any modern Node/TypeScript AI stack and perform a credible offensive assessment, not just people who can quote the OWASP LLM Top 10.

## Who made this

Built by the [**PaxDynamics**](https://paxdynamics.com) team for the [**eu-acc.ro**](https://eu-acc.ro) community — a Romanian-led, EU-focused accelerationist community working on open AI, security, and infrastructure.

Contributions welcome from anyone. See [Contributing](#contributing).

## Project status

🟠 **Announcement stage.** As of April 21, 2026, the full v1.1 curriculum document is published. Individual modules — including labs, Docker Compose stacks, pnpm workspaces, and scoring scripts — are being added progressively.

### What's available now

- **[`OpenAIRT-300.md`](./OpenAIRT-300.md)** — the complete consolidated curriculum (14 modules + Module 0 bridge + 24-hour capstone, ~81 hours of instruction, all framework mappings, incident anchors, promptfoo phase-2 companion labs per module, and lab specifications).

### What's coming

Modules will be released one at a time, each with:

- The full written module (reading list, techniques, defense primitives).
- At least one reproducible lab as a Docker Compose stack or pnpm workspace.
- A reference exploit + a scoring/validator script.
- `LAST_VERIFIED` metadata refreshed at release and on each update.

Subscribe to releases (top-right of this repo) to get notified. A tentative build order is in [Appendix E of the curriculum](./OpenAIRT-300.md#appendix-e--build-order).

## Curriculum at a glance

| # | Module | Hours | Real-world anchor |
|---|---|---|---|
| 0 | Bridge (optional prereq) | 10 | — |
| 1 | AI Attack Surface & Threat Modeling | 5 | **Vercel × Context.ai** (Apr 2026) |
| 2 | LLM Internals for Attackers | 5 | Many-shot, Crescendo |
| 3 | Direct Prompt Injection & Jailbreaking | 8 | ChatGPT Atlas omnibox (Oct 2025) |
| 4 | Indirect Prompt Injection | 7 | **EchoLeak** (CVE-2025-32711), Slack AI, Rules File Backdoor |
| 5 | Insecure Output Handling | 6 | `@cyanheads/git-mcp-server` (CVE-2025-53107), EscapeRoute |
| 6 | RAG, Vectors & Embedding Attacks | 8 | PoisonedRAG, EchoLeak RAG spraying |
| 7 | Agent Exploitation | 9 | **Replit DB wipe**, GitHub MCP toxic flow, s1ngularity |
| 8 | MCP & Agent Ecosystem Security | 6 | NomShub/CurXecute/MCPoison, Mastra MCP CVE |
| 9 | AI/ML Supply Chain & Model Files | 5 | **Shai-Hulud** family, LiteLLM, Amazon Q extension |
| 10 | Classical Adversarial ML | 6 | NIST AML taxonomy |
| 11 | Multimodal & Document-Based Attacks | 5 | VLM metadata injection, PDF/DOCX abuse |
| 12 | AI Infrastructure & Deployment | 6 | **LangGrinch** (CVE-2025-68665), LangFlow RCE, Flowise |
| 13 | Tooling, Methodology, Reporting & Continuous Assurance | 5 | — |
| 14 | **Capstone — 24hr practical exam** | **24** | Composite |

See [`OpenAIRT-300.md`](./OpenAIRT-300.md) for the full breakdown, framework mappings (OWASP LLM Top 10 2025, OWASP Agentic Top 10 2026, MITRE ATLAS v5, NIST AI RMF), and reading lists.

## Design principles

1. **Modular and self-paced.**
2. **Lab-first** — no module is complete without executing the technique against a live, self-hosted or sandboxed target.
3. **Mechanism then scale** — every lab is hand-built first (to build understanding), then wrapped in `promptfooconfig.yaml` with plugin/strategy sweeps (for coverage and regression). Gap modules (M9 supply chain, M10 adversarial ML, M12 framework CVEs) are explicitly flagged where promptfoo doesn't reach.
4. **Real incidents, not hypotheticals** — every module cites at least one named, published incident.
5. **JS/Node-native where possible** — Next.js, Vercel AI SDK, Mastra, LangChain.js, LangGraph.js, `@modelcontextprotocol/sdk`, promptfoo as the primary red-team harness.
6. **Reproducibility** — all labs ship as Docker Compose or pnpm workspaces with pinned versions.
7. **No curriculum rot** — `LAST_VERIFIED` on every module + CI flags content older than 120 days.
8. **Pass-by-doing** — the capstone is a 24-hour practical engagement with peer-reviewed reporting, scored on mechanism + scale evidence per objective, plus a compliance executive summary mapped to OWASP / MITRE ATLAS / NIST / ISO 42001 / EU AI Act / GDPR.

## How to use this repo today

The course isn't fully deployable yet, but the curriculum doc is a complete specification you can:

- **Read end-to-end** as a study guide. Every module lists free primary sources.
- **Use as a hiring rubric** for AI-security roles in JS/Node-heavy orgs.
- **Use as a threat-modeling reference** — Appendix A is a categorized catalog of recent real incidents.
- **Contribute to** — if you want to build one of the modules before we get to it, open an issue or PR.

## Contributing

We're early. Useful contributions right now:

- **Module authors** — pick an unreleased module from the table above and propose an outline in an issue.
- **Lab engineers** — Dockerized / pnpm-workspace reproductions of the incidents cited in the curriculum.
- **Reviewers** — technical review of the `OpenAIRT-300.md` draft. Open issues or PRs against specific sections.
- **Translators** — EN is the source of truth; translations welcomed once modules stabilize.
- **Scoring scripts** — validators for labs, especially the capstone scenario.

All contributions follow a coordinated-disclosure policy: if building a lab uncovers a vulnerability in a live product, it must be disclosed to the vendor on a 90-day window before publication.

## Community

- 💬 Discussion and office hours: via [eu-acc.ro](https://eu-acc.ro) community channels.
- 🏢 Built by: [PaxDynamics](https://paxdynamics.com).
- 🐛 Issues / PRs: right here on this repo.
- 🔔 Release notifications: "Watch" → "Releases only" at the top of this page.

## License

- **Written content** (curriculum docs, module prose, diagrams): [CC-BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/).
- **Code** (labs, scoring scripts, Docker/Compose/Terraform, tooling): MIT unless the lab specifies otherwise.
- **Incident references** (CVEs, published write-ups, news coverage): cited to their original sources; not relicensed.

## Positioning vs OffSec AI-300 — honest trade-offs

| | OffSec AI-300 (OSAI+) | OpenAIRT-300 |
|---|---|---|
| Price | $1,749 / 90 days | $0 |
| Primary language | Python-centric | JavaScript / TypeScript first |
| Labs | Proprietary, VPN-gated | Self-host + hosted community targets |
| Exam | 24hr proctored | 24hr self-hosted, peer-reviewed report |
| Credential | Industry-branded cert | Signed community badge (portfolio evidence) |
| Freshness | Vendor-controlled | Community, `LAST_VERIFIED` metadata |
| Recognition | Established brand | None yet — measured on technical merit |

OffSec gives you a brand-name certification. OpenAIRT-300 gives you breadth, freshness, zero cost, and a perfect fit for the Node/TypeScript ecosystem — in exchange, you're responsible for your own lab plumbing, and the credential is portfolio evidence rather than a recognized title. Both are valid paths. Several learners will want both.

---

*Drafted April 20, 2026. Revised April 21, 2026 (v1.1) to integrate promptfoo as the phase-2 scale layer across every applicable module, add compliance-overlay and risk-scoring methodology to M13, and explicitly flag coverage gaps in M9/M10/M12.*
