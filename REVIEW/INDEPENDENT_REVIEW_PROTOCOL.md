# Independent Review Protocol — AetherHuman v1.0.0

**Status:** Protocol — not yet executed.
**Date:** 2026-11-17
**Version:** 1.0.0
**Author of the materials under review:** Samir Baladi
**ORCID:** 0009-0003-8903-0029
**License:** CC-BY-4.0
**DOI:** 10.5281/zenodo.24278322

---

## 0. Purpose

This protocol specifies how an independent external reviewer evaluates **AetherHuman**, the eleventh candidate of the Aether family, currently paused at Phase 4 — **(E) Undetermined (interim)**.

The purpose is to determine whether AetherHuman should be:

- **(A)** Accepted as an independent architectural dimension
- **(R)** Rejected
- **(F)** Folded into an existing dimension
- **(D)** Deferred for an external reason
- **(E)** Kept at (E) Undetermined, with a named missing test

The review does **not** attempt to confirm the candidate. It attempts to **falsify** its claims, and to judge whether the existing failure conditions are sufficient.

---

## 1. Independence criteria

A reviewer is *independent* only if:

- [ ] They are not the author.
- [ ] They are not a direct collaborator of the author.
- [ ] They have no financial or institutional stake in the outcome.
- [ ] They have not been promised any benefit for a particular outcome.
- [ ] They have not previously endorsed or rejected the candidate in a public forum.

If any of the above is not met, the review is **internal**, not independent, and must be labeled as such.

---

## 2. Materials provided to the reviewer

- `ARCHITECTURAL_HYPOTHESIS.md`
- `research/RESPONSIBILITY_BOUNDARIES.md`
- `FALSIFICATION/FALSIFICATION_PLAN.md`
- `DECISIONS/INDEPENDENCE_DECISION.md`
- `REVIEW/INTERNAL_REVIEW.md`
- `paper/AetherHuman_Research_Paper_v1.0.0.pdf`
- The DOIs of the seven foundational dimensions and the three candidates (AetherIdentity, AetherPolicy, AetherAudit)

---

## 3. Review tracks

### Track A — Boundary Overlap Audit

**Question.** Can the functions of AetherHuman (Fn1–Fn5) be fully absorbed into existing dimensions (AetherGovern + AetherIdentity + AetherRuntime + others)?

**Deliverable.** A coverage matrix (functions × dimensions) with a "remainder" column, and a written justification for each cell.

### Track B — Proposition Stress Testing

**Question.** Can P1 and P2 be formalized, proved, or falsified?

- P1 — Determinism of human intervention semantics.
- P2 — Irreducible human authority anchor.

**Deliverable.** For each proposition, one of:
- (i) A formal proof.
- (ii) A counterexample.
- (iii) A statement that the proposition is not formalizable as stated.

### Track C — Observable Benefit (H-F4)

**Question.** Is there a measurable benefit to separating AetherHuman from AetherGovern + AetherIdentity + AetherRuntime?

**Deliverable.** A measurement design (scenarios S1–S6, metrics M1–M6, baselines B1–B3), and — if feasible — preliminary measurements. If measurement is not feasible, a statement of what would be required.

### Track D — Contradiction and Citation Audit

**Question.** Are there contradictions, unsupported claims, or fabricated citations?

**Deliverable.** A list of findings, each with file, line, claim, problem, and recommended action.

---

## 4. Review outcomes

| Outcome | Meaning | Consequence |
|:-:|---|---|
| **(A)** Accept | Survives all four failure conditions. | Phase 5 permitted. |
| **(R)** Reject | At least one condition falsified. | Candidate closed. |
| **(F)** Fold | All functions fold into existing dimensions. | Candidate absorbed. |
| **(D)** Defer | Review cannot be completed for an external reason. | Remains at Phase 4. |
| **(E)** Undetermined | Cannot falsify, cannot measure benefit. | Remains at Phase 4. |

---

## 5. What the reviewer is asked NOT to do

- Do not confirm the candidate. The goal is to falsify.
- Do not propose implementation. Phase 5 and 6 are not permitted.
- Do not rewrite the manuscript. The review is not an editorial pass.
- Do not sign off on independence without a Track C measurement (or an explicit statement that Track C is not feasible).

---

## 6. Deliverables

The reviewer provides:

1. Reviewer declaration (independence, conflict of interest).
2. Completed Track deliverables (one or more of A, B, C, D).
3. Outcome for AetherHuman (A / R / F / D / E).
4. Open questions that the review could not resolve.

The author then:

1. Records the review in `REVIEW/INDEPENDENT_REVIEW.md`.
2. Updates `ROADMAP.md` (Phase 2 → ✅ Complete).
3. Updates `DECISIONS/INDEPENDENCE_DECISION.md` (if the outcome changes).
4. Re-deploys the site.

---

## 7. What this protocol does not claim

- That the reviewer will accept or reject the candidate.
- That the reviewer will complete all four tracks.
- That the outcome will change.

The protocol claims only that the review is **independent**, **documented**, and **bounded** by the same falsification-first methodology as the candidate itself.

---

**AetherHuman v1.0.0 — Independent Review Protocol**
© 2026 Samir Baladi — Ronin Institute / Rite of Renaissance
DOI: [10.5281/zenodo.24278322](https://doi.org/10.5281/zenodo.24278322)
