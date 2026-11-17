# AetherHuman — Complete Inventory

**Version:** 2.0.0 (Architectural Investigation)
**Release Date:** 2026-11-17
**Author:** Samir Baladi
**Email:** gitdeeper@gmail.com
**ORCID:** [0009-0003-8903-0029](https://orcid.org/0009-0003-8903-0029)
**License:** CC-BY-4.0 (docs, manuscript, figures) · MIT (code, future — none in this release)
**Status:** Architectural Investigation · Candidate (Phase 4: undetermined)
**Record ID:** AETHERHUMAN-01
**DOI (Zenodo):** 10.5281/zenodo.24278322
**DOI (Figshare):** Pending
**DOI (GitHub Release):** v1.0.0
**Website:** [aetherhuman.netlify.app](https://aetherhuman.netlify.app)

---

## Research Status

| Item | Status |
|---|---|
| Document type | Research article (architectural hypothesis + decision) |
| Paper (v1.0.0) | ⏳ Pending publication |
| Implementation | ❌ Not built (not permitted at Phase 4) |
| Tests | ❌ None |
| Experiments | ❌ None executed |
| PyPI package | ❌ Not published |
| Real-world deployment | None |
| Propositions P1–P2 | Stated with proof sketches; not machine-checked |
| Failure conditions | H-F1–H-F3 not falsified by argument; H-F4 untested; H-F2 most fragile |
| Internal review | ✅ Complete (`REVIEW/INTERNAL_REVIEW.md`) |
| Independent review | ✅ Complete (`REVIEW/INDEPENDENT_REVIEW.md`) — Confirmed by Jonathan Rabe (2026-11-17) |
| Independent review protocol | ✅ Complete (`REVIEW/INDEPENDENT_REVIEW_PROTOCOL.md`) |
| Review status | Not peer reviewed |
| Decision | **(E) Undetermined (interim)** |

---

## Repository Links

| Platform | URL | Role | Status |
|----------|-----|------|--------|
| GitHub | https://github.com/gitdeeper15/aetherhuman | Primary | ⏳ Pending |
| GitHub Release | https://github.com/gitdeeper15/aetherhuman/releases/tag/v1.0.0 | Release v1.0.0 | ⏳ Pending |
| GitLab | https://gitlab.com/gitdeeper15/aetherhuman | Mirror | ⏳ Pending |
| Codeberg | https://codeberg.org/gitdeeper15/aetherhuman | Mirror | ⏳ Pending |
| Bitbucket | https://bitbucket.org/gitdeeper15/aetherhuman | Mirror | ⏳ Pending |
| Website | https://aetherhuman.netlify.app | Live documentation | ⏳ Pending |
| Zenodo | https://doi.org/10.5281/zenodo.24278322 | Citable DOI | ✅ Published |
| Figshare | Pending | Preprint archive | ⏳ Pending |
| ORCID | https://orcid.org/0009-0003-8903-0029 | Identity | ✅ Active |

---

## Root Files

| File | Purpose | Status |
|------|---------|:-:|
| `.gitignore` | Git ignore rules | ✅ |
| `AUTHORS.md` | Contributors | ✅ |
| `CHANGELOG.md` | Version history | ✅ |
| `CITATION.cff` | Citation metadata | ✅ |
| `CONTRIBUTING.md` | Contribution guidelines | ✅ |
| `INVENTORY.md` | This file | ✅ |
| `LICENSE` | CC-BY-4.0 (docs) + MIT (code, future) | ✅ |
| `PROJECT_SUMMARY.txt` | One-page summary | ✅ |
| `README.md` | Main documentation | ✅ |
| `ARCHITECTURAL_HYPOTHESIS.md` | The hypothesis under investigation | ✅ |
| `ROADMAP.md` | Phase status (0 → 6) | ✅ |
| `VERSION` | `1.0.0` | ✅ |
| `manifest.json` | Project manifest | ✅ |
| `scientific_state.json` | Scientific state record | ✅ |
| `netlify.toml` | Netlify configuration | ✅ |

---

## Directories

| Directory | Contents | Status |
|-----------|----------|:-:|
| `docs/figures/` | 9 figures (Fig1–Fig9) | ⏳ Pending |
| `research/` | `RESPONSIBILITY_BOUNDARIES.md` | ✅ Complete |
| `FALSIFICATION/` | `FALSIFICATION_PLAN.md` | ✅ Complete |
| `DECISIONS/` | `INDEPENDENCE_DECISION.md` | ✅ Complete (interim) |
| `REVIEW/` | `INTERNAL_REVIEW.md` (internal) | ✅ Complete |
| `REVIEW/` | `INDEPENDENT_REVIEW.md` (template) | ✅ Complete |
| `REVIEW/` | `INDEPENDENT_REVIEW_PROTOCOL.md` (protocol) | ✅ Complete |
| `REVIEW/` | `README.md` (directory guide) | ✅ Complete |
| `REFERENCES/` | To be populated with references from the paper | 🔄 In progress |
| `REPORTS/architectural_investigation/` | `investigation_report.md` | ✅ Complete |
| `paper/` | `AetherHuman_Research_Paper_v1.0.0.md` | ⏳ Draft |
| `PUBLICATION/Netlify/public/` | Website (4 HTML pages + robots/sitemap) | ⏳ Pending |

No `src/`, no `tests/`, no `experiments/` — and none is planned unless Phase 4 becomes positive.

---

## Formal Artifacts

| Category | Count |
|---|---|
| Functions (Fn1–Fn5) | 5 |
| Failure Conditions (H-F1 to H-F4) | 4 |
| Propositions (P1–P2, proof sketches) | 2 |
| Boundaries (Govern, Identity, Runtime, Audit, Policy, Git, Flow, Proof, Mesh, Orchestrate) | 10 |
| Open Questions (Q1–Q10) | 10 |
| Figures | 9 |
| References | TBD |
| Related Aether projects | 11 (including AetherHuman) |
| Phases | 7 (0–6) |
| Tests run | 0 |
| Experiments executed | 0 |

---

## Failure Conditions (H-F1 to H-F4)

| ID | Claim under test | Status |
|:-:|---|:-:|
| H-F1 | Non-redundancy | 🟡 Not falsified (author's reading) |
| H-F2 | Distinction from Govern + Identity + Runtime | 🟡 Not falsified (remainder may be small; **most fragile**) |
| H-F3 | Decentralizability | 🟡 Not falsified (residuals: veto, mandatory intervention) |
| H-F4 | Observable benefit | 🔴 **Untested** |

> "Not falsified" is weaker than "confirmed". "Untested" is not a pass. The decision rule requires **all four** to be tested with none falsified.

---

## Phase Status

| Phase | Description | Status |
|---|---|---|
| 0 | Architectural Hypothesis | ✅ Complete |
| 1 | Responsibility Mapping | ✅ Complete |
| 2 | Hypothesis Review (Independent) | ✅ Complete (Confirmed by Jonathan Rabe) |
| 3 | Falsification Design | ✅ Complete |
| 4 | Independence Decision | ⚠️ Interim: (E) undetermined |
| 5 | Architectural Specification | ❌ Not permitted |
| 6 | Reference Implementation | ❌ Not permitted |

---

## Companion Works

AetherHuman is the **eleventh project (candidate)** of the Aether family. It does **not** replace AetherGovern, AetherIdentity, or AetherAudit.

| # | System | Dimension | Status | DOI |
|:-:|---|---|---|---|
| 1 | AetherGit | Storage / Foundation | Foundational | [10.5281/zenodo.23976986](https://doi.org/10.5281/zenodo.23976986) |
| 2 | AetherFlow | Integration | Foundational | [10.5281/zenodo.23979129](https://doi.org/10.5281/zenodo.23979129) |
| 3 | AetherProof | Verification | Foundational | [10.5281/zenodo.24013124](https://doi.org/10.5281/zenodo.24013124) |
| 4 | AetherMesh | Decentralization | Foundational | [10.5281/zenodo.24038038](https://doi.org/10.5281/zenodo.24038038) |
| 5 | AetherGovern | Governance | Foundational | [10.5281/zenodo.24054524](https://doi.org/10.5281/zenodo.24054524) |
| 6 | AetherRuntime | Runtime Assurance | Foundational | [10.5281/zenodo.24078477](https://doi.org/10.5281/zenodo.24078477) |
| 7 | AetherOrchestrate | Orchestration | Foundational | [10.5281/zenodo.24095399](https://doi.org/10.5281/zenodo.24095399) |
| 8 | AetherIdentity | Identity | Candidate | [10.5281/zenodo.24102739](https://doi.org/10.5281/zenodo.24102739) |
| 9 | AetherPolicy | Policy Lifecycle | Candidate | [10.5281/zenodo.24160047](https://doi.org/10.5281/zenodo.24160047) |
| 10 | AetherAudit | Audit / Evidence / Accountability | Candidate | [10.5281/zenodo.24274628](https://doi.org/10.5281/zenodo.24274628) |
| 11 | **AetherHuman** | **Human Participation / Authority / Intervention** | **Candidate (this repository)** | **[10.5281/zenodo.24278322](https://doi.org/10.5281/zenodo.24278322)** |

---

## What This Repository Does Not Claim

- That AetherHuman is an independent architectural dimension.
- That the five functions are complete, independent, or necessary.
- That the boundaries with AetherGovern, AetherIdentity, AetherRuntime, and the other dimensions are sufficient.
- That the gap is genuine.
- That implementation should begin.
- Any observed benefit (H-F4 is untested).
- Any causal effect.

---

## Citation

### Paper (v1.0.0)

```bibtex
@techreport{baladi2026aetherhuman,
  author       = {Baladi, Samir},
  title        = {AetherHuman: Human Participation in Autonomous Agent Ecosystems},
  institution  = {Ronin Institute / Rite of Renaissance},
  type         = {Research Paper},
  year         = {2026},
  month        = {November},
  version      = {1.0.0},
  doi          = {10.5281/zenodo.24278322},
  url          = {https://doi.org/10.5281/zenodo.24278322},
  note         = {Architectural investigation; Phase 4 (undetermined)}
}
```

---

Contact

· Email: gitdeeper@gmail.com
· ORCID: 0009-0003-8903-0029
· Website: aetherhuman.netlify.app
· GitHub: gitdeeper15/aetherhuman

---

Last Updated: 2026-11-17
Current Version: 1.0.0
Decision: (E) Undetermined (interim)
