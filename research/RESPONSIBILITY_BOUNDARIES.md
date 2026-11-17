# AetherHuman — Responsibility Boundaries

**Version:** 1.0.0
**Date:** 2026-11-17
**Status:** Phase 1 — Complete
**Author:** Samir Baladi
**ORCID:** 0009-0003-8903-0029
**License:** CC-BY-4.0
**DOI:** 10.5281/zenodo.24278322

---

## 1. Purpose

This document maps the five functions of AetherHuman (Fn1–Fn5) against the ten existing dimensions of the Aether family, to determine what, if anything, remains after composition. It does not decide independence. It records the author's reading, for attack in Phase 2.

---

## 2. The Ten Existing Dimensions

| # | Dimension | Primary Responsibility |
|:-:|---|---|
| 1 | AetherGit | Storage and versioning |
| 2 | AetherFlow | Integration |
| 3 | AetherProof | Verification |
| 4 | AetherMesh | Distribution and consistency |
| 5 | AetherGovern | Governance authority |
| 6 | AetherRuntime | Runtime assurance |
| 7 | AetherOrchestrate | Orchestration |
| 8 | AetherIdentity | Identity and continuity |
| 9 | AetherPolicy | Policy lifecycle and enforcement |
| 10 | AetherAudit | Evidence and accountability |

---

## 3. Coverage Matrix

Legend: ● full · ◐ partial · ○ none

| Dimension | Fn1 Principal | Fn2 Authority | Fn3 Intervention | Fn4 Accountability | Fn5 Boundary |
|:-:|:-:|:-:|:-:|:-:|:-:|
| AetherGit | ○ | ○ | ○ | ◐ | ○ |
| AetherFlow | ○ | ○ | ○ | ○ | ○ |
| AetherProof | ○ | ○ | ○ | ○ | ○ |
| AetherMesh | ○ | ○ | ○ | ○ | ○ |
| AetherGovern | ◐ | ◐ | ◐ | ◐ | ◐ |
| AetherRuntime | ○ | ○ | ◐ | ○ | ○ |
| AetherOrchestrate | ○ | ○ | ○ | ○ | ○ |
| AetherIdentity | ◐ | ◐ | ○ | ○ | ○ |
| AetherPolicy | ○ | ◐ | ○ | ○ | ○ |
| AetherAudit | ○ | ○ | ○ | ◐ | ○ |
| **AetherHuman** | ● | ● | ● | ● | ● |

---

## 4. Remainders by Function

### Fn1 — Human Principal Representation
- **Govern** treats a human as a source of authority (root of a delegation graph).
- **Identity** can carry a human as an agent of a special type.
- **Remainder:** the three properties H1 attributes to a human principal — non-specifiability, non-continuous availability, termination of responsibility — are not carried by either.

### Fn2 — Authority Relation
- **Govern** represents delegated authority.
- **Policy** represents enforcement and override.
- **Remainder:** the relationship among the four forms (delegated, oversight, veto, independent) is not defined by either. Whether veto is a delegation or an independent anchor is the open question (H2).

### Fn3 — Intervention Semantics
- **Runtime** can trigger a pause and wait for a response.
- **Remainder:** the meaning of no response, and the semantics of concurrent intervention requests, are not supplied by runtime. The absence rule is the residual case.

### Fn4 — Accountability Chain
- **Audit** attributes responsibility across agent delegations.
- **Remainder:** the restriction of attribution to a human principal, with the effectiveness condition of Definition 5, may be a restriction of Audit's function rather than an independent one. This is flagged as the weakest remainder (see H4).

### Fn5 — Human-Agent Boundary
- **Govern** defines what agents may do.
- **Remainder:** the boundary that keeps human decision and agent autonomy from collapsing into each other is not defined by any single dimension. Whether it is architectural or a property of use is open.

---

## 5. The Most Fragile Boundary

**H-F2** is the most fragile condition because:
- Most of what AetherHuman would use is supplied by Govern, Identity, and Runtime.
- The remainder may be small after composition.
- Fn4 in particular may reduce to a restriction of AetherAudit.

The author's reading: H-F2 is **not falsified** by argument, but the remainder is small.

---

## 6. What This Document Does Not Do

- It does not decide independence.
- It does not claim the matrix is complete.
- It does not claim the coverage is correct beyond the author's reading.
- It does not evaluate AetherHuman against external related work (see the paper, Section 2).

---

## 7. Next Step

Phase 2 (Independent Review) must examine this matrix. The reviewer is asked to attack the remainders, in particular the Fn4 remainder, and to state whether any survives.

---

**AetherHuman v1.0.0 — Responsibility Boundaries**
© 2026 Samir Baladi — Ronin Institute / Rite of Renaissance
DOI: [10.5281/zenodo.24278322](https://doi.org/10.5281/zenodo.24278322)
