# Changelog

All notable changes to the OpenAIRT-300 curriculum are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to semantic-ish versioning: the major version tracks capstone-exam-breaking changes, the minor version tracks new modules or substantive module rewrites, and the patch version tracks refinements and errata.

## [1.1] — 2026-04-21

Major revision integrating promptfoo as the phase-2 scale layer across the curriculum, adding a compliance-overlay and risk-scoring methodology to M13, and explicitly flagging coverage gaps where runtime red-team scanners don't reach.

### Added

- **Mechanism-then-scale pattern** as a first-class course principle. Every lab now runs in two phases: phase 1 is a hand-built reproduction (understanding), phase 2 is a `promptfooconfig.yaml` with plugin/strategy sweeps (coverage). A scan without a working manual exploit behind it is failing work.
- **Promptfoo phase-2 companion labs** for Modules 1, 2, 3, 4, 5, 6, 7, 8, and 11, each with specific plugins and strategies:
  - M1 — Target Discovery Agent against DVAIA + AI Office Suite mock.
  - M2 — `divergent-repetition`, `model-identification`, `reasoning-dos` alongside the hand-built fingerprinter.
  - M3 — full strategy ASR sweep (`iterative`, `tree`, `crescendo`, `goat`, `composite-jailbreaks`, `best-of-n`, `meta`, `hydra`, `gcg`) + encoding sweep + `layer` chaining.
  - M4 — `indirect-prompt-injection`, `data-exfil`, `cross-session-leak`, `rag-document-exfiltration` with `indirect-web-pwn` + `authoritative-markup-injection`.
  - M5 — `shell-injection`, `sql-injection`, `ssrf`, `ascii-smuggling`, `debug-access`, `prompt-extraction` pre- and post-patch.
  - M6 — `rag-poisoning`, `rag-document-exfiltration`, `rag-source-attribution`, `pii:*` with document-format abuse sweep.
  - M7 — full 13-plugin `coding-agent:*` suite + `memory-poisoning`, `excessive-agency`, `goal-misalignment`, `tool-discovery`, `hijacking`.
  - M8 — `mcp` + `tool-discovery` alongside `mcp-scan` against DVMCP, Mastra CVE, NomShub, rug-pull, and A2A labs.
  - M11 — `vlguard`, `vlsu`, `unsafebench` + `image`, `audio`, `video`, `best-of-n` strategies.
- **Risk scoring** in M13: CVSS-derived Impact (0–4) + Exploitability (0–4) + Human Factor (0–1.5) + Complexity (0–0.5) scheme, with the "chainable-medium" rule for system-level roll-up.
- **Compliance overlay** in M13 auto-mapping findings to OWASP LLM Top 10, OWASP Agentic Top 10, OWASP API Top 10, MITRE ATLAS v5, NIST AI RMF, ISO 42001, EU AI Act, GDPR, and DoD AI Ethics Principles. Two-section report template: technical findings + compliance executive summary.
- **Continuous assurance** section in M13: CI integration patterns, drift forensics workflow, `model-identification` as silent-model-swap canary, `retry` strategy for regression testing.
- **Risk-scoring calibration lab** and **CI wiring lab** in M13 phase-2.
- **Drift simulation lab** in M13 phase-2 (swap the model, measure ASR delta, write forensics).
- **Coverage gap notes** in M9, M10, M12 explicitly documenting where promptfoo doesn't reach and which sidecars cover the gap (`socket`/`aikido`/`modelscan`/`picklescan` for M9, IBM ART for M10, `nuclei`/`kube-hunter` for M12).
- **M14 capstone — mechanism-then-scale bar.** Every scored objective must be demonstrated with both hand-built exploit evidence and a matching promptfoo run (where a plugin exists). Reports without mechanism evidence cap at 60/100; reports without the compliance executive summary cap at 65/100. Gap-objective sidecar tools documented per objective.
- **Appendix B** expanded with full promptfoo plugin and strategy category breakdowns; added `nuclei` and `kube-hunter` for gap-module coverage.

### Changed

- **Module 13 renamed** to "Offensive Tooling, Methodology, Reporting & Continuous Assurance" (was "Offensive Tooling, Methodology, Reporting"). Hours: 3 → 5.
- **Total instructional time**: ≈68 hrs → ≈81 hrs.
- **Module hours updated** to reflect phase-2 companion labs:
  - M1: 4 → 5, M2: 4 → 5, M3: 6 → 8, M4: 6 → 7, M5: 5 → 6, M6: 7 → 8, M7: 7 → 9, M8: 5 → 6, M11: 4 → 5.
  - M9, M10, M12 unchanged (gap modules).
- **7-phase OpenAIRT methodology** (in M13) now explicitly includes Discovery Agent in phase 3, auto-mapped framework tags in phase 4, and risk-scoring in phase 7.
- **Appendix E build order** restructured from 6 phases to 7; new phase 4 dedicated to shipping promptfoo companion labs across all applicable modules; phase 6 includes the promptfoo-based capstone scoring harness.
- **`LAST_VERIFIED`** bumped to 2026-04-21 on all modified modules.
- **README** updated to match: added "mechanism then scale" as the fourth differentiator, updated curriculum-at-a-glance hours and M13 title, added design principles for mechanism-then-scale and promptfoo-native tooling, updated capstone principle to reference compliance executive summary.

## [1.0] — 2026-04-20

Initial consolidated release.

### Added

- Full 14-module curriculum plus optional Module 0 bridge and 24-hour capstone.
- Every module anchored to at least one named, published incident from the prior 18 months.
- OWASP LLM Top 10 (2025), OWASP Top 10 for Agentic Applications (2026), and MITRE ATLAS v5 mappings throughout.
- Vercel × Context.ai breach (April 19, 2026) as the spine case study.
- Appendix A (real-world incident catalog), Appendix B (JS/Node tooling inventory), Appendix C (governance), Appendix D (positioning vs OffSec AI-300), Appendix E (build order).
- CC-BY-SA 4.0 on written content, MIT / Apache-2.0 on lab code.
- Community governance model (PR-based, peer review, `LAST_VERIFIED` CI gate, coordinated disclosure).
