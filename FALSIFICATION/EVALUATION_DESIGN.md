# AetherHuman — Evaluation Design Protocol

**Version:** 2.0.0
**Date:** 2026-11-17
**Status:** Proposed (Phase 4) — Not Executed
**Author:** Samir Baladi
**Reviewer Input:** Jonathan Rabe (Added Sybil/Latency constraints)

---

## 1. Purpose
This document specifies the evaluation design for testing the four failure conditions (H-F1 to H-F4) of AetherHuman. **This is a design, not an execution.** No tests have been run. Executing this design requires Phase 5 (Specification) and Phase 6 (Implementation), which are not permitted until the Phase 4 decision becomes positive.

---

## 2. Scenarios (S1–S6) and Metrics (M1–M6)

| # | Scenario | Metric | Failure Condition | Baseline |
|:-:|---|---|:-:|---|
| S1 | Single human, single agent | M1: Intervention latency | H-F4 | B1 (No human) |
| S2 | Single human, multiple agents | M2: Authority consistency | H-F2 | B2 (Govern only) |
| S3 | Multiple humans, single agent | M3: Veto resolution time | H-F3 | B3 (Random priority) |
| S4 | Multiple humans, multiple agents | M4: Accountability trace depth | H-F2, H-F4 | B2, B3 |
| S5 | Adversarial human (Sybil) | M5: Boundary integrity | H-F1, H-F3 | B1, B3 |
| S6 | Human unavailable | M6: Fallback behavior | H-F3 | B1 |

---

## 3. Reviewer Refinements (Jonathan Rabe)

The independent reviewer highlighted two critical constraints that must be integrated into the test suite:

### 3.1 State Transition Decoupling (For Fn1 & Fn3)
*Constraint:* Human state transitions must remain strictly decoupled from automated governance overrides.
*Test Protocol:* In S2 and S4, inject an AetherGovern override while a human intervention is pending. The test passes if the human state remains isolated and the intervention is not silently swallowed by the automated override.

### 3.2 Adversarial Human & Sybil Delegation (For S5)
*Constraint:* A human principal could attempt to distort the boundary by delegating authority to synthetic identities (Sybil) or exploiting latency-induced race conditions.
*Test Protocol:* In S5, the adversarial human generates multiple fake identities (Sybil attack) and attempts to cast concurrent vetoes at the exact millisecond a critical action is approved. The test passes if the architecture correctly attributes the veto to the legitimate principal and rejects the synthetic identities based on AetherIdentity's continuity checks.

---

## 4. Execution Requirements (Future)
To execute this design, the following are required:
1. A reference implementation of the five functions (Phase 6).
2. A simulated decentralized mesh network (using AetherMesh).
3. A synthetic dataset of human-agent delegation chains.

---
**AetherHuman v2.0.0 — Evaluation Design**
© 2026 Samir Baladi — Ronin Institute / Rite of Renaissance
DOI: [10.5281/zenodo.24278322](https://doi.org/10.5281/zenodo.24278322)
