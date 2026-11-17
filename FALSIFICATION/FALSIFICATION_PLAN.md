# AetherHuman — Falsification Plan

**Version:** 1.0.0
**Date:** 2026-11-17
**Status:** Phase 3 — Complete
**Author:** Samir Baladi
**ORCID:** 0009-0003-8903-0029
**License:** CC-BY-4.0
**DOI:** 10.5281/zenodo.24278322

---

## 1. Purpose

This plan specifies how the four failure conditions H-F1 to H-F4 of AetherHuman are to be tested. It does not run the tests. It states, for each condition, what would falsify it, what evidence would count, and what the current status is.

---

## 2. The Four Failure Conditions

| ID | Claim | Status |
|:-:|---|:-:|
| H-F1 | Non-redundancy: not covered by Govern / Identity / Runtime | 🟡 Not falsified |
| H-F2 | Distinction from Govern + Identity + Runtime | 🟡 Not falsified (most fragile) |
| H-F3 | Decentralizability: no central human authority | 🟡 Not falsified (residuals) |
| H-F4 | Observable benefit | 🔴 Untested |

---

## 3. Falsification Conditions

### H-F1 — Non-redundancy

**Claim:** Human participation is not already covered by AetherGovern, AetherIdentity, or AetherRuntime.

**What would falsify it:**
- A demonstration that each of Fn1–Fn5 is fully representable by one of the three neighbours.
- A demonstration that the union of Govern + Identity + Runtime covers all five functions without remainder.

**Evidence that would count:**
- A formal reduction of the five functions to the three neighbours.
- A worked example in which a human participation case is fully handled by the three, with no residual requirement.

**Current status:** Not falsified by argument. The responsibility boundaries (Phase 1) show partial coverage but not full.

**Residual risk:** Related work outside the family (Cheng & Cheng; HDP) overlaps Fn1/Fn4. This is a reservation on H-F1, recorded in the paper, Section 2.

---

### H-F2 — Distinction from Govern + Identity + Runtime

**Claim:** Even when the three neighbours are composed, a remainder survives.

**What would falsify it:**
- A demonstration that the remainder after composition is empty.
- A demonstration that every remainder identified in Phase 1 is either (i) supplied by one of the three, or (ii) not architectural.

**Evidence that would count:**
- A worked case in which the composition of the three handles all five functions with no residual requirement.
- A proof that Fn4 reduces entirely to AetherAudit's attribution function.

**Current status:** Not falsified by argument, but the remainder is small. This is the most fragile condition.

**Residual risk:** The Fn4 remainder may reduce to a restriction of AetherAudit.

---

### H-F3 — Decentralizability

**Claim:** No central human authority is required for the five functions.

**What would falsify it:**
- A demonstration that veto or mandatory intervention cannot be enforced without a central decision point.
- A demonstration that the absence rule for Fn3 requires a central arbiter.

**Evidence that would count:**
- A proof that veto in a decentralized population requires a central enforcer.
- A construction showing that mandatory intervention can be enforced by local rules alone.

**Current status:** Not falsified by argument, with residuals: veto and mandatory intervention are residual cases not yet shown to be decentralizable.

---

### H-F4 — Observable Benefit

**Claim:** AetherHuman yields an observable benefit over the existing dimensions.

**What would falsify it:**
- A measurement showing no significant difference between AetherHuman and the composition of Govern + Identity + Runtime on the six scenarios of the evaluation design.
- A demonstration that the benefit cannot be operationalized.

**Evidence that would count:**
- Execution of the six scenarios (S1–S6) with the six metrics (M1–M6).
- Comparison against baselines B1–B3.

**Current status:** Untested. No experiment has been run. Section 9 of the paper is a proposal, not a result.

---

## 4. The Evaluation Design (Proposal)

| # | Scenario | Metric | Failure Condition Tested |
|:-:|---|---|---|
| S1 | Single human, single agent | M1: Intervention latency | H-F4 |
| S2 | Single human, multiple agents | M2: Authority consistency | H-F2 |
| S3 | Multiple humans, single agent | M3: Veto resolution time | H-F3 |
| S4 | Multiple humans, multiple agents | M4: Accountability trace depth | H-F2, H-F4 |
| S5 | Adversarial human | M5: Boundary integrity | H-F1, H-F3 |
| S6 | Human unavailable | M6: Fallback behavior | H-F3 |

**Baselines:** B1–B3 (defined in the paper).
**Hypotheses:** H1–H5 (working hypotheses for the five functions; none established).
**Remainders:** R1–R3 (open).

This design has not been executed. Executing it requires Phase 5 (Specification) and Phase 6 (Implementation), which are not permitted until the independence decision becomes positive.

---

## 5. What This Plan Does Not Do

- It does not run any test.
- It does not claim that any condition has been tested.
- It does not claim that the evaluation design is sufficient.
- It does not claim that H-F4 is measurable as stated.

---

## 6. Next Step

Phase 2 (Independent Review) must examine this plan. The reviewer is asked to attack the falsification conditions themselves, in particular whether they are testable and whether the evaluation design would distinguish AetherHuman from the composition of the three neighbours.

---

**AetherHuman v1.0.0 — Falsification Plan**
© 2026 Samir Baladi — Ronin Institute / Rite of Renaissance
DOI: [10.5281/zenodo.24278322](https://doi.org/10.5281/zenodo.24278322)
