# AetherHuman — Stronger Argument Memo for H-F2

**Version:** 3.0.0
**Status:** Complete
**Scope:** Internal Architectural Analysis
**Related Project:** AetherHuman v2.0.0
**Target Condition:** H-F2 — Architectural Remainder
**Current Architectural Decision:** (E) Undetermined (interim)
**Decision Authority:** External Review
**Execution Status:** Phase 5 and Phase 6 remain unauthorized.

---

## 1. Purpose and Decision Boundary

This memo examines whether a stronger architectural argument can address H-F2, the most fragile condition in the current AetherHuman independence assessment.

Its purpose is to determine whether the four remaining functions — Fn1, Fn3, Fn4, and Fn5 — contain architectural responsibilities that cannot be adequately represented by AetherGovern, AetherIdentity, and AetherRuntime.

This memo does not:

- Change the Phase 4 decision.
- Authorize Phase 5 or Phase 6.
- Establish AetherHuman as an independent architectural dimension.
- Treat the existence of an uncovered function as sufficient proof of architectural independence.
- Replace the external review process.

The existing decision (E) Undetermined (interim) remains unchanged.

## 2. H-F2 — Precise Reformulation

H-F2 asks whether a genuine architectural remainder exists after accounting for the responsibilities already represented by AetherGovern, AetherIdentity, and AetherRuntime.

The investigation must distinguish three possibilities:

1. **Full Coverage:** The existing dimensions can represent the function without introducing a distinct architectural responsibility.
2. **Partial Coverage:** Existing dimensions cover part of the function, but a residual responsibility remains.
3. **Architectural Remainder:** The residual responsibility requires a distinct architectural model, invariant, or execution semantics that cannot be adequately represented by the existing dimensions.

A function is not considered independent merely because it has a different name, data structure, or implementation.

The central question is whether its responsibility remains architecturally distinct after a complete reduction analysis.

## 3. Fn1 — Human Principal Representation

### 3.1 Original Function

> *"How is a human represented as an architectural principal (not merely an agent of a special type)? The wording of the supplied statement already contains the hypothesis that a human principal is more than a labelled agent. What the function leaves open is what the extra is: whether it is a property of the representation (for example, that a human principal is not replicable), a property of the relation to the architecture (that the architecture can only observe it), or merely a name."*

### 3.2 Original Hypothesis

> *"A human principal differs from an agent in at least three respects that a representation must carry: the architecture cannot specify or instantiate its behaviour; its availability cannot be assumed to be continuous; and responsibility for outcomes terminates at it. Whether these differences require a representation that an agent identity record cannot carry is not established."*

### 3.3 Reduction Analysis

The hypothesis proposes three candidate distinctions. Each must be tested separately against existing dimensions.

#### 3.3.1 Non-specifiability of behavior

**Claim:** The architecture cannot specify or instantiate a human's behavior, while it can specify and instantiate an agent's behavior.

**Reduction test against AetherIdentity:**
AetherIdentity represents an agent through properties: a DID, a continuity record, a reputation history. Can it represent a party whose behavior is **not** a property it controls?

AetherIdentity does not, in principle, prescribe what an agent *does* — it prescribes what an agent *is* and *has been*. However, every identity record in the current family assumes a subject that can be queried, re-instantiated, or reconstructed. A human principal cannot be re-instantiated by the architecture, but this is a property of the *observer's* capabilities, not necessarily of the identity record itself.

*Preliminary observation:* Non-specifiability may be a fact about the relationship between the architecture and the human, not a property the identity record must carry. Whether this requires a distinct representation is not established by the function alone.

#### 3.3.2 Non-continuous availability

**Claim:** A human's availability cannot be assumed continuous, unlike an agent's.

**Reduction test against AetherRuntime and AetherGovern:**
Runtime already handles agents that are unavailable, crashed, or partitioned — availability is not assumed for agents either. Governance can express a delegation that requires an external party's response.

**The relevant distinction is therefore not availability versus unavailability, but whether the architecture must assign different semantics to different causes of unavailability. No such requirement has yet been established.**

*Preliminary observation:* Non-continuous availability is not unique to humans in the existing dimensions. Agents can also be unavailable. Whether the *reason* for unavailability matters architecturally (e.g., a human is absent by choice or incapacity, not by failure) is a distinct question not yet addressed.

#### 3.3.3 Responsibility termination

**Claim:** Responsibility for outcomes terminates at a human principal; it does not terminate at an agent.

**Reduction test against AetherGovern and AetherAudit:**
Governance can express that a delegation chain ends at a principal. Audit can attribute responsibility to the human at the root of a chain.

However, the *termination* of responsibility is not the same as the *attribution* of responsibility. Attribution records who is responsible; termination asserts that no further delegation exists beyond this party.

*Preliminary observation:* Termination may be a property that Fn1 and Fn4 share. Whether it is architecturally distinct from the attribution already supported by AetherAudit is a question for Section 6, not for Fn1 in isolation.

### 3.4 Cross-Cutting Question

The three proposed distinctions (non-specifiability, non-continuous availability, responsibility termination) may not be independent of each other. If responsibility termination is the only architecturally load-bearing distinction, then Fn1's case reduces to a subset of Fn4's case, which in turn depends on Section 6's analysis of AetherAudit.

This possibility must be recorded, not resolved.

### 3.5 Candidate Architectural Responsibility

Two candidate responsibilities survive the preliminary reduction, but neither is established:

1. **A representation of a party the architecture cannot instantiate or prescribe.** This is a semantic claim about what can be represented, not about how it is stored.
2. **An architectural distinction between a party whose unavailability is *chosen* or *inherent* and a party whose unavailability is *failure*.** This distinction would matter only if the architecture treats these two cases differently.

Neither candidate is a confirmed remainder. Both are recorded for Section 7.

### 3.6 Assessment

| Aspect | Status |
|---|---|
| Non-specifiability as an architectural requirement | Open — may be a relationship property, not a representation property |
| Non-continuous availability as a distinct requirement | Open — likely reducible to Runtime unless "reason for unavailability" matters |
| Responsibility termination as a distinct requirement | Open — overlaps with Fn4; must be resolved with Section 6 |
| Independence of the three distinctions from each other | Not established — they may collapse to one |
| Whether any of the above requires a representation that AetherIdentity cannot carry | Not established |

**Status:** Open.

**Note:** This section does not conclude that Fn1 is independent or reducible. It records the analytical state at the end of the reduction test.

## 4. Fn3 — Intervention Semantics

### 4.1 Original Function

> *"How does human intervention affect execution — optional, conditional, or mandatory non-bypassable? An optional intervention may be made and is not required. A conditional intervention is required when a stated condition holds. A mandatory intervention is required, and no path of execution may proceed without it. The function leaves open what the semantics are when no human responds, what happens to intervention requests that are made concurrently by several agents, and what it means for an intervention to be non-bypassable when there is no central enforcer."*

### 4.2 Original Hypothesis

> *"The three modes, together with a rule for the absence of a response, define the effect of an intervention on an execution by a deterministic function of the specification and the record of responses. The absence rule is the part that agent-to-agent semantics do not supply, because agents are assumed to respond. This hypothesis is supported only in the weak sense of Proposition P1."*

### 4.3 Reduction Analysis

The hypothesis contains four distinct elements. Each must be tested separately.

#### 4.3.1 The three modes (optional, conditional, mandatory)

**Reduction test against AetherGovern and AetherRuntime:**
AetherGovern already distinguishes between what is permitted, forbidden, and required. A conditional intervention (required when a condition holds) is structurally similar to a conditional policy in Governance. A mandatory intervention (no path of execution may proceed without it) is structurally similar to a hard gate in Governance.

**Preliminary observation:** The three modes themselves are not new. They are expressible in terms of existing governance primitives. The question is not whether the *modes* exist, but whether the *subject* of the modes is architecturally distinct.

#### 4.3.2 The absence rule

**Reduction test against AetherGovern and AetherRuntime:**
This is the strongest element of the hypothesis. The hypothesis claims that *"the absence rule is the part that agent-to-agent semantics do not supply, because agents are assumed to respond."*

Two sub-questions arise:

1. **Do agents actually always respond?** In practice, agents can fail silently. If agents can fail silently, then absence of a response is not unique to humans — it applies to agents too. The hypothesis's claim that agents are "assumed to respond" may be an assumption, not a property.

2. **If agents can fail silently, what distinguishes a human's non-response?** The human may be *choosing* not to respond, or may be *unable* to respond. Neither choice nor inability is specific to humans — agents can be designed to choose not to respond (e.g., a policy that says "no action is the correct action").

**The absence of a response is an observable execution condition, but it is not necessarily equivalent to an explicit response. Agents can also enter this condition through crashes, timeouts, or silent failures.**

**Preliminary observation:** The absence rule is not established as a distinct architectural responsibility. It may be expressible in AetherGovern (a policy that defines what happens on timeout) and AetherRuntime (a monitor that detects the timeout).

#### 4.3.3 Concurrent intervention requests

**Reduction test against AetherOrchestrate and AetherRuntime:**
Concurrent requests from multiple parties are a coordination problem. Orchestrate handles concurrency; Runtime handles execution ordering.

**Preliminary observation:** Concurrent intervention requests may be reducible to orchestration and runtime primitives. The question of *conflict resolution* — what happens when two human principals issue contradictory interventions — is a governance matter, not a distinct architectural responsibility.

#### 4.3.4 Non-bypassability without a central enforcer

**Reduction test against AetherGovern and AetherMesh:**
This is the most structurally demanding element. The hypothesis asks: *"what it means for an intervention to be non-bypassable when there is no central enforcer."*

Non-bypassability in a decentralized system requires either:
- A consensus mechanism (Mesh-level).
- A cryptographic commitment that agents cannot break without detection (Governance-level).
- An architectural invariant that every agent must uphold (a state-transition rule).

**Detectability of bypass is not equivalent to prevention of bypass. Likewise, consensus among participating agents does not by itself establish non-bypassability if execution can proceed outside the agreed mechanism.**

The question is whether any of these is sufficient to express *human* non-bypassability, or whether human non-bypassability requires something the existing dimensions cannot express.

**Preliminary observation:** This is the element of Fn3 most likely to survive reduction. If human interventions must be non-bypassable even when agents are adversarial, this may require a distinct architectural invariant — but the current analysis does not establish that the invariant must be *human-specific*.

### 4.4 Cross-Cutting Question

The four elements of Fn3 are not independent of one another:

- The three modes presuppose an intervention that has already been received.
- The absence rule is what governs the case when no intervention arrives.
- **Concurrent intervention requests introduce a separate conflict-resolution problem. They must not be conflated with the absence of a response, although both may require explicit execution semantics.**
- Non-bypassability is a property of the *mode* itself, not a separate element.

If the four elements collapse into two (modes + non-bypassability) or even one (a non-bypassable human intervention), then the analytical burden on Fn3 is smaller than the hypothesis suggests — but so is the candidate architectural responsibility.

This possibility must be recorded, not resolved.

### 4.5 Candidate Architectural Responsibility

Two candidate responsibilities survive the preliminary reduction, but neither is established:

1. **A non-bypassable execution boundary that holds in a decentralized, potentially adversarial system.** This is a candidate because it requires an architectural invariant that no existing dimension has been shown to provide *specifically for human interventions*. It might be reducible to AetherGovern + AetherMesh, but the reduction has not been performed.

2. **An absence-rule semantics that distinguishes "the human did not respond" from "the agent did not respond."** This is a candidate only if the architecture must treat these two cases differently. No argument yet establishes that it must.

Neither candidate is a confirmed remainder. Both are recorded for Section 7.

### 4.6 Assessment

| Aspect | Status |
|---|---|
| The three modes (optional, conditional, mandatory) | Open — expressible in Governance primitives |
| The absence rule as a distinct requirement | Open — agents can also fail silently; may be reducible |
| Concurrent intervention requests | Open — likely reducible to Orchestrate + Runtime |
| Non-bypassability without a central enforcer | Open — strongest candidate for a distinct invariant; not yet shown to be human-specific |
| Whether any of the above requires a distinct architectural responsibility | Not established |

**Status:** Open.

**Note:** This section does not conclude that Fn3 is independent or reducible. It records the analytical state at the end of the reduction test.

## 5. Fn5 — Human-Agent Boundary

### 5.1 Original Function

> *"How is the boundary between human decision and agent autonomy maintained without collapsing one into the other? Two collapses are possible. In one, the agents' autonomy is reduced to the execution of human decisions, and the ecosystem ceases to be autonomous in the sense the other dimensions assume. In the other, the human's decisions are reduced to a signal that agents process, and the human participates only nominally. The function leaves open what keeps the two apart and whether the boundary is a property of an architecture or of its use."*

### 5.2 Hypothesis Status

**No independent hypothesis is explicitly stated for Fn5 in the original paper.**

The original hypothesis in the paper addresses Fn1, Fn3, and Fn4. For Fn5, the paper states the function and the two collapse scenarios but does not state a testable hypothesis.

This absence is recorded, not repaired by inventing a hypothesis retrospectively. The absence itself is analytically significant: Fn5 is the function for which the paper made the weakest architectural commitment.

### 5.3 Reduction Analysis

The function identifies two collapse scenarios. Each must be tested separately.

#### 5.3.1 Collapse toward agent-execution (agents become executors of human decisions)

**Claim:** If agents merely execute human decisions, the ecosystem ceases to be autonomous.

**Reduction test against AetherGovern and AetherOrchestrate:**
Governance already distinguishes between authority (who may decide) and execution (who performs). An agent that executes a decision under delegation is still an agent — it has authority to act, even if the action is determined by the principal. **Delegated execution authority does not, by itself, establish meaningful agent autonomy. The relevant question is whether the agent retains decision-making discretion within the delegated scope.**

The question is whether *meaningful autonomy* requires the agent to have discretion that cannot be overridden by the human. If it does, the boundary is a property of the governance model (a policy that limits human override). If it does not, the collapse is a description of a deployment configuration, not an architectural property.

**Preliminary observation:** The collapse toward agent-execution is a property of the governance configuration, not necessarily a distinct architectural responsibility. It may be expressible in Governance without introducing a new invariant.

#### 5.3.2 Collapse toward nominal participation (human decisions become ordinary agent inputs)

**Claim:** If human decisions are processed by agents like any other input, human participation becomes nominal.

**Reduction test against AetherIdentity, AetherGovern, and AetherRuntime:**
The human's decision can be tagged with an identity (the human), represented as an event (with a source), and processed by governance (with the authority to act on it). This is what the existing dimensions already do.

The question is whether the *meaning* of the human's decision — its status as an authoritative decision rather than an input signal — can be preserved without a distinct architectural mechanism.

This is where the phrase "property of an architecture or of its use" becomes load-bearing. If the boundary is a property of use (i.e., a deployment practice), it is not an architectural responsibility. If it is a property of architecture, it must be expressible as an invariant that the architecture enforces.

**Preliminary observation:** The collapse toward nominal participation is the more architecturally demanding scenario, but the paper does not state what would distinguish a decision from an input. This is an open semantic question, not an established architectural requirement.

#### 5.3.3 The unresolved question of the boundary

The function explicitly asks: *"whether the boundary is a property of an architecture or of its use."* This question is not resolved in the paper, and the reduction analysis cannot resolve it either. It is a question about what kind of thing the boundary is.

If the boundary is a property of use, it belongs to deployment practice and does not require an architectural dimension.

If the boundary is a property of architecture, it requires an invariant that the architecture enforces. No such invariant is currently stated.

### 5.4 Cross-Cutting Question

The two collapse scenarios are not symmetric:

- The first collapse (agents → executors) can be prevented by limiting human authority in the governance model.
- The second collapse (humans → inputs) can be prevented only by preserving a distinction between authoritative decision and input signal.

If the second collapse is the only one that requires architectural work, then Fn5's burden rests entirely on a distinction that the paper does not formalize.

This possibility must be recorded, not resolved.

### 5.5 Candidate Architectural Responsibility

Two candidate responsibilities survive the preliminary reduction, but neither is established:

1. **A distinction between an authoritative human decision and an agent input signal, enforced by the architecture.** This is a candidate only if the distinction is architecturally enforceable. The paper leaves this open.

2. **An architectural constraint defining the respective decision-making boundaries of human principals and agents, such that neither authority automatically collapses the other's role. This is a candidate only if the boundary is an architectural invariant rather than a governance policy. The paper does not establish this.**

Neither candidate is a confirmed remainder. Both are recorded for Section 7.

### 5.6 Assessment

| Aspect | Status |
|---|---|
| No explicit hypothesis stated for Fn5 | Recorded — the absence itself is analytically significant |
| Collapse toward agent-execution | Open — may be a governance configuration, not an architectural invariant |
| Collapse toward nominal participation | Open — the distinction between decision and input is not formalized |
| Whether the boundary is architectural or a property of use | Not established |
| Whether any of the above requires a distinct architectural responsibility | Not established |

**Status:** Open.

**Note:** This section does not conclude that Fn5 is independent or reducible. It records the analytical state at the end of the reduction test.

## 6. Fn4 — Accountability Chain

### 6.1 Original Function

> *"How is human responsibility attributed and traced across agent delegations? The function overlaps most with the accountability attribution examined in the AetherAudit record [10], which asks the same kind of question of evidence and of delegation chains in general. The distinction the present paper draws is that Fn4 concerns where a chain ends: in a human, and with what warrant, so that responsibility is neither lost in a chain of agents nor assigned to a human who had no means of acting differently [24, 16]. The distinction may be a restriction of the audit function to one kind of principal, and in that case Fn4 is not independent of AetherAudit."*

### 6.2 Original Hypothesis

> *"The end of an accountability chain is a human principal only when participation is effective in the sense of Definition 5. A rule that assigns responsibility to a human by form alone is an attribution rule and not an accountability chain. Whether the distinction is architectural or merely a policy for attribution is not established."*

### 6.3 Reduction Analysis

The hypothesis contains three elements. Each must be tested separately.

#### 6.3.1 The human as terminus of the chain

**Reduction test against AetherAudit:**
AetherAudit already traces delegation chains and attributes responsibility. The question is whether AetherAudit's attribution can terminate at a human principal as readily as it terminates at an agent principal.

AetherAudit's own Definition 4 in the paper states that "the rule that decides answerability is supplied from outside the chain." This suggests that AetherAudit is agnostic about who is at the terminus — an agent, a human, or any other principal type.

**Preliminary observation:** The human as terminus is not, in itself, a distinct architectural responsibility. It is a property of the accountability chain that AetherAudit already accommodates. Whether the *warrant* for termination differs when the terminus is human is a separate question (see 6.3.2).

#### 6.3.2 Effective participation as a condition

**Reduction test against AetherAudit and AetherGovern:**
The hypothesis states that termination at a human is warranted only when participation is "effective" in the sense of Definition 5. This introduces a substantive condition: the human must have had the information and means to decide differently.

This is a *policy* condition on the attribution, not necessarily an *architectural* condition. Governance can express a policy that says "responsibility terminates at a human only if X, Y, Z conditions are met." Audit can then apply that policy during attribution.

However, if the conditions of effective participation cannot be expressed in any existing policy language — if they require a new architectural primitive — then a distinct responsibility is warranted. No argument yet establishes that they do.

**Preliminary observation:** Effective participation may be expressible as a governance policy on accountability attribution. Whether it requires a new architectural primitive is not established.

#### 6.3.3 The distinction between attribution rule and accountability chain

**Reduction test against AetherAudit:**
The hypothesis claims that a rule assigning responsibility to a human by form alone is an attribution rule, not an accountability chain. This is a claim about the *meaning* of the chain, not about its structure.

If AetherAudit can distinguish between "responsibility attributed because a name is attached" and "responsibility attributed because the person was in a position to act differently", then the distinction is a policy on audit, not a new dimension.

If it cannot — if the distinction is architecturally inexpressible — then a distinct architectural responsibility exists. No argument yet establishes that it is inexpressible.

**Preliminary observation:** This distinction may be expressible in the audit policy. The claim that it cannot be is not established.

### 6.4 AetherAudit's Unresolved Status

**Question:** Does AetherAudit's own unresolved status affect the analysis of Fn4?

**Analysis:**

AetherAudit is itself a candidate at (E) Undetermined (interim). It has not been shown to be independent. Its own architecture has not been proven to cover the accountability functions it claims.

**Two implications follow:**

1. If AetherAudit is eventually shown to be independent, this does not automatically establish that it provides the effective-participation condition. Its terminus-agnosticism does not, by itself, establish that it addresses the conditions of human responsibility.

2. If AetherAudit is eventually shown to be reducible, this does not mean that its function disappears; it means that its coverage, if established, is attributed to the dimensions that absorbed it.

**Implication:** AetherAudit's unresolved status introduces a dependency into the coverage analysis of Fn4, but it does not make all analysis of Fn4 impossible before AetherAudit is resolved. Fn4 can be examined conditionally against the possible outcomes of AetherAudit's own assessment.

### 6.5 Candidate Architectural Responsibility

One candidate responsibility survives the preliminary reduction, but it is not established:

1. **A human-specific condition of effective participation that is architecturally enforced, not merely policy-declared.** This is a candidate only if the condition cannot be expressed as a policy in the existing dimensions. The paper does not establish this.

A second candidate was considered and provisionally treated:

2. **The human as terminus of the accountability chain — provisionally treated as potentially reducible to AetherAudit, given its apparent terminus-agnostic structure. Whether this generic treatment adequately captures the human-specific conditions identified in Fn4 remains open.**

The remaining candidate is conditional on AetherAudit's resolution, as described in 6.4.

### 6.6 Assessment

| Aspect | Status |
|---|---|
| Human as terminus of chain | Likely reducible to AetherAudit (which is terminus-agnostic) |
| Effective participation as a condition | Open — may be expressible as a governance policy |
| Attribution rule vs. accountability chain distinction | Open — may be expressible in audit policy |
| Whether any of the above requires a distinct architectural responsibility | Not established |
| **Dependency on AetherAudit's unresolved status** | **Significant — Fn4 cannot be resolved before AetherAudit is resolved** |

**Status:** Open, with a structural dependency on AetherAudit.

**Note:** This section does not conclude that Fn4 is independent or reducible. It records the analytical state at the end of the reduction test, and it records the structural dependency that makes Fn4's status conditional.

## 7. Remainder Assessment

### 7.1 Purpose

Sections 3–6 examined each function separately. This section examines whether the candidate responsibilities identified across the four functions are:

1. **Independent of one another** (each represents a distinct architectural responsibility), or
2. **Overlapping** (several functions express the same underlying responsibility), or
3. **Fragmented** (each function's remainder is too small to matter individually, and there is no shared underlying responsibility).

The distinction matters because H-F2 asks whether *a* genuine architectural remainder exists — not whether *four* exist.

### 7.2 Collective Table

| Function | Existing coverage examined | Candidate architectural responsibility | Evidence status | Assessment |
|:-:|---|---|---|---|
| **Fn1** | Govern + Identity | (a) Representation of a party the architecture cannot instantiate or prescribe. (b) Distinction between chosen/inherent unavailability and failure. | Analytical only | Open |
| **Fn3** | Govern + Runtime | (a) Non-bypassable execution boundary in a decentralized system. (b) Absence-rule semantics distinguishing human from agent non-response. | Analytical only | Open |
| **Fn4** | AetherAudit + Govern + Identity | Human-specific condition of effective participation that is architecturally enforced, not merely policy-declared. | Analytical only; conditional on AetherAudit | Open |
| **Fn5** | Govern + Runtime + Orchestrate | (a) Distinction between authoritative human decision and agent input signal, architecturally enforced. (b) Boundary of decision-making between human and agent, such that neither collapses the other. | Analytical only | Open |

### 7.3 Cross-Functional Analysis

#### 7.3.1 Possible overlaps

Several candidate responsibilities across the four functions may express the same underlying architectural concern:

**Overlap A — The distinction between decision and signal.**

**Fn1's representation of a party whose behaviour the architecture cannot instantiate concerns the status of the represented principal. Fn5's distinction between an authoritative human decision and an agent input signal concerns the authority and semantic status of decisions. Fn4's effective-participation condition concerns the warrant under which responsibility may terminate at a human principal. These concerns may be related, but their equivalence has not been established.**

If these three are expressions of one underlying concern, then the candidate remainder is smaller than the sum of three separate functions would suggest.

**Potential Interaction B — Non-bypassability and principal representation.**

- Fn3's "non-bypassable execution boundary" is a claim about enforcement.
- Fn5's "boundary of decision-making such that neither authority collapses the other" is also a claim about enforcement.
- **Fn1's non-instantiable representation and Fn3's non-bypassable execution boundary may interact, but no necessary dependency between them has been established.**

If non-bypassability is the single architectural concern underlying Fn3, Fn5, and part of Fn1, then these three may not represent three independent remainders.

**Overlap C — Human-specific accountability.**

- Fn4's "effective participation" condition is a claim about when responsibility terminates at a human.
- Fn1's "responsibility termination" is the same terminus, seen from the representation side.
- **Fn1 concerns the representation and termination point of responsibility, whereas Fn4 concerns the conditions that warrant such termination. The two may be complementary rather than identical. Whether their combined requirements introduce a distinct architectural responsibility remains open.**

If these two are the same concern, then Fn4 and Fn1 may collapse into one candidate remainder.

#### 7.3.2 Possible fragmentation

Alternatively, each function's remainder may be genuine but too small to matter individually. If Fn1's remainder is a representation property that does not affect execution, and Fn3's remainder is an execution property that does not affect representation, and Fn4's remainder is a policy condition that does not affect either, then the four functions do not together form a coherent architectural concern.

The paper's claim is that the five functions form *"a coherent architectural concern"* (Section 5). This claim has not been tested. The collective analysis in this section is the first test of that claim.

#### 7.3.3 Possible coherence

A third possibility is that the four functions, taken together, express a single coherent architectural concern that none of them expresses alone. For example, the combination of human representation (Fn1), non-bypassable intervention (Fn3), effective accountability (Fn4), and the human-agent boundary (Fn5) might together constitute the architecture's treatment of a human *as a principal whose authority is structurally distinct from that of an agent*.

**This formulation is illustrative and does not constitute a proposed definition of AetherHuman or a conclusion about its independence.**

Whether this coherence is genuine or merely narrative is a question the analysis cannot yet answer. No evidence currently establishes or refutes it.

### 7.4 The Question of Counting

The paper's argument for H-F2 does not depend on the number of independent remainders. It depends on whether *any* genuine architectural remainder exists.

However, the number matters for a different reason: if four remainders collapse to one, the candidate's architectural claim is smaller than it appears. If four remainders are genuinely independent, the candidate's claim is stronger.

The analysis in this section does not resolve this counting question. It records that the question exists and that the current evidence does not answer it.

### 7.5 Candidate Remainder Status (Collective)

| Candidate remainder | Status |
|---|---|
| Overlap A — Decision vs. signal | Possible overlap; not yet established |
| Overlap B — Non-bypassability | Possible overlap; Fn3's remainder is strongest on this axis |
| Overlap C — Human-specific accountability | Possible overlap; conditional on AetherAudit's resolution |
| Independent remainder (each function separately) | Not established |
| Coherent unified remainder | Not established |
| Fragmentary remainder (each too small to matter) | Not established |

**Collective Status:** Open.

**Note:** This section does not conclude that a genuine architectural remainder exists, nor that it does not exist. It records the analytical state after the cross-functional analysis, including the unresolved questions about overlap, fragmentation, and coherence.

## 8. Impact on H-F2 and H-F4

### 8.1 Purpose

This section evaluates what the analysis in Sections 3–7 means for the two conditions that govern AetherHuman's status:

- **H-F2** — the existence of an architectural remainder after composition.
- **H-F4** — the observable benefit of that remainder.

This section does not change the Phase 4 decision. It records what the analysis has and has not established.

### 8.2 Impact on H-F2

#### 8.2.1 What H-F2 requires

H-F2 asks whether a genuine architectural remainder exists after accounting for AetherGovern, AetherIdentity, and AetherRuntime.

The question is not whether AetherHuman *could* have a remainder, but whether the analysis demonstrates that it *does*.

#### 8.2.2 What the analysis has established

The analysis has established the following:

- Each of the four functions contains candidate architectural responsibilities that are not yet fully reducible to existing dimensions.
- The candidate responsibilities overlap in ways that are not fully resolved.
- No candidate responsibility has been shown to be architecturally distinct in the sense that would satisfy H-F2.

The analysis has **not** established the following:

- That any candidate responsibility is a confirmed architectural remainder.
- That the overlap between candidate responsibilities collapses to a single coherent responsibility.
- That the analysis is complete — the reduction tests are preliminary.

#### 8.2.3 Possible outcomes for H-F2

| Outcome | Meaning | Status |
|---|---|---|
| **Supported** | The analysis identifies at least one residual architectural responsibility that cannot be reduced to existing dimensions. | Not established |
| **Not Supported** | The existing dimensions adequately represent all examined responsibilities. | Not established |
| **Undetermined** | Available analysis does not establish either conclusion. | **Currently the case** |

#### 8.2.4 Conclusion for H-F2

**The condition remains Undetermined, but the analytical basis is now more specific: identifiable candidate responsibilities have been isolated, their possible overlaps have been recorded, and the principal unresolved reduction questions have been made explicit.**

The analysis has strengthened the *candidate* remainders (particularly in Fn3's non-bypassability and Fn5's decision-signal distinction), but it has not established H-F2.

### 8.3 Impact on H-F4

#### 8.3.1 What H-F4 requires

H-F4 asks whether the remainder, if it exists, produces an observable architectural benefit. Unlike H-F2, which is analytical, H-F4 is empirical — it requires measurement.

#### 8.3.2 What the analysis has not established

The analysis in this memo is analytical throughout. It has not:

- Measured any benefit.
- Demonstrated that any candidate remainder produces a benefit.
- Established that a benefit, if it exists, would be observable.

#### 8.3.3 Relationship between H-F2 and H-F4

The two conditions are independent in kind:

- H-F2 is a claim about the structure of the architecture.
- H-F4 is a claim about the effect of that structure.

A memo can strengthen H-F2 without touching H-F4 (which is what this memo has done).

A memo cannot strengthen H-F4 without measurement — no amount of analysis can substitute for the experiment required.

#### 8.3.4 Conclusion for H-F4

**H-F4 remains untested.** The analytical work in this memo cannot change that status.

### 8.4 What Would Move the Analysis Forward

Two separate questions would move the analysis forward:

**For H-F2:**
- A formal reduction test that demonstrates whether the candidate responsibilities (particularly Fn3's non-bypassability and Fn5's decision-signal distinction) can or cannot be expressed in existing dimensions.
- A resolution of the overlap question (7.3.1), either by showing that the overlaps are genuine collapses or by showing that they are distinct.

**For H-F4:**
- Execution of the evaluation design (S1–S6).
- Measurement of the benefits that the analysis suggests might exist.

**Further internal analysis of H-F2 may proceed without changing the current decision. If the resulting argument is intended to support a reassessment of Phase 4, the memo should be submitted to the available external reviewer through a separate formal request. This memo itself does not constitute that request.**

**H-F4 requires the execution of the evaluation design (S1–S6), subject to the project's authorization requirements for Phases 5 and 6. External review does not substitute for experimental execution or automatically authorize those phases.**

### 8.5 Conclusion

The analysis has:

- **Strengthened H-F2** from an undifferentiated "not established" to a state where specific candidate remainders have been identified and can be examined.
- **Not changed H-F4**, which remains untested and requires empirical work.

The Phase 4 decision remains **(E) Undetermined (interim)**. The memo does not constitute a change in decision. It records a strengthening of the analytical basis on which the decision rests.

**Assessment:** H-F2 (strengthened, not supported); H-F4 (unchanged, untested).

## 9. External Review Recommendation

### 9.1 Purpose

This section states what the analysis recommends regarding external review. It does not itself constitute a request to the external reviewer. It records what, if anything, should be submitted to the reviewer for reassessment.

### 9.2 Has the H-F2 Argument Materially Strengthened?

**Yes, in a limited sense.**

The analysis has moved the H-F2 argument from an undifferentiated "not established" to a state in which:

- Specific candidate responsibilities have been identified in each of the four functions.
- The overlaps between these candidates have been recorded.
- The reduction tests for each candidate have been made explicit.
- The principal unresolved questions (overlap, counting, coherence) have been named.

This is a material strengthening of the *analytical basis* for H-F2. It is not a material strengthening of *the H-F2 claim itself*, which remains unestablished.

### 9.3 Which Functions Retain a Credible Architectural Remainder?

Based on the analysis in Sections 3–7:

| Function | Credible candidate? | Assessment |
|:-:|---|---|
| **Fn1** | Yes, provisionally | The non-specifiability and responsibility-termination candidates survive preliminary analysis but may collapse into Fn4's analysis. |
| **Fn3** | Yes, provisionally | Non-bypassability in a decentralized system is the strongest single candidate. It has not been shown to be *human-specific* or irreducible to Govern + Mesh. |
| **Fn4** | Yes, conditionally | The effective-participation condition is a candidate, but its status is conditional on AetherAudit's own resolution. |
| **Fn5** | Yes, provisionally | The decision-signal distinction is a candidate but lacks an explicit hypothesis in the original paper. |

**All four remain candidate architectural responsibilities following preliminary analysis. None has yet been established as an irreducible architectural remainder.**

### 9.4 Which Functions Are Likely Reducible?

Based on the analysis, several elements within each function appear likely to be reducible to existing dimensions:

| Element | Likely reduction |
|---|---|
| Fn1's non-continuous availability | AetherRuntime (availability is not assumed for agents either) |
| Fn3's three modes | AetherGovern (optional, conditional, mandatory are expressible as policies) |
| Fn3's concurrent intervention requests | AetherOrchestrate (coordination) |
| Fn4's human-as-terminus (provisional) | AetherAudit (terminus-agnostic) |
| Fn5's collapse toward agent-execution | AetherGovern (configurable via policy) |

**These reductions are preliminary.** They show *possible* reduction paths, not *established* ones. The analysis records them so that the reduction test for each is explicit.

### 9.5 Is the Collective Remainder Coherent or Fragmented?

**Not established either way.**

The analysis has recorded both possibilities:

- **Coherence:** The four functions might together express a single coherent concern (human as a structurally distinct principal).
- **Fragmentation:** The remainders might each be too small to matter individually, without forming a coherent whole.

No evidence currently establishes or refutes either possibility. The counting question (7.4) is not resolved by the analysis.

### 9.6 Should the Memo Be Submitted for External Reassessment?

**This depends on the purpose of the submission.**

**If the purpose is to change the Phase 4 decision from (E) to (A) or (R):**

- The memo does not, by itself, establish sufficient grounds for changing the Phase 4 decision. The reviewer would need to assess whether the strengthened analytical basis warrants any reassessment.

**If the purpose is to communicate the strengthened analytical basis to the reviewer:**

- The memo is appropriate for that purpose.
- It could inform the reviewer's understanding of what remains unresolved.
- It would not constitute a formal request for reassessment (see 9.7).

**If the purpose is to record the analysis in the project's own documentation:**

- The memo serves that purpose regardless of external submission.

### 9.7 Formal Request Required

**If the memo recommends external reassessment, a separate formal request must be sent to the reviewer. This memo itself does not constitute that request.**

The formal request would need to specify:

1. Which conclusions the author is asking the reviewer to reassess.
2. What new evidence (if any) has been introduced since the previous review.
3. Whether the author believes the Phase 4 decision should change, and on what basis.
4. Whether the author is asking the reviewer to issue a new review or to update the previous one.

None of these are in the memo itself. The memo is analytical; the request is procedural.

### 9.8 What Remains Unresolved

The following remain unresolved after this memo:

| # | Unresolved item |
|:-:|---|
| 1 | Whether any candidate remainder is confirmed as architecturally distinct |
| 2 | Whether the overlaps in 7.3.1 are genuine collapses or distinct concerns |
| 3 | Whether the four functions express one coherent concern or fragments |
| 4 | Whether Fn4's status can be resolved independently of AetherAudit's status |
| 5 | Whether the candidate remainders can be reduced to existing dimensions with further analysis |
| 6 | Whether H-F4 (empirical benefit) can be established through execution of S1–S6, subject to the project's authorization requirements for Phases 5 and 6. |
| 7 | Whether the analytical basis, if submitted, would persuade the reviewer to reassess |

### 9.9 Recommendation Summary

The memo recommends:

1. **Retain the current decision (E) Undetermined (interim).** The analysis has strengthened the candidate remainders but has not established them.
2. **Consider submitting the memo to the available external reviewer to communicate the strengthened analytical basis and invite an assessment of the unresolved questions. If formal reassessment of the Phase 4 decision is sought, a separate formal request is required.**
3. **Do not treat the memo as authorizing Phase 5 or Phase 6.** Those remain unauthorized.
4. **Record the memo as an internal analytical artifact** in the project's documentation, regardless of external submission.
5. **Identify the next analytical step** — either a formal reduction test on one candidate remainder (most likely Fn3's non-bypassability) or a resolution of the overlap question.

### 9.10 Decision Status Note

The Phase 4 decision remains **(E) Undetermined (interim)**. The recommendation of this memo is to retain that decision, not to change it.

If external reassessment is eventually pursued, it would proceed according to the project's established methodology, with a separate formal request to the reviewer.

## 10. Decision Status

### 10.1 Current Decision

**Current Decision:** (E) Undetermined (interim).

This is the decision recorded in `DECISIONS/INDEPENDENCE_DECISION.md` for AetherHuman v2.0.0 and confirmed by the external reviewer (Jonathan Rabe, 2026-11-17). This memo does not change that decision.

### 10.2 Phase Authorization

| Phase | Status | Note |
|:-:|---|---|
| Phase 5 — Architectural Specification | **Not authorized** | Requires a positive Phase 4 decision |
| Phase 6 — Reference Implementation | **Not authorized** | Requires Phase 5 |

The memo does not authorize either phase. Neither is authorized by any conclusion in this memo.

### 10.3 Effect of This Memo

**This memo is analytical only. It has no automatic effect on the Phase 4 decision.**

Specifically:

- It does not change the decision from (E) to (A) or (R).
- It does not authorize Phase 5 or Phase 6.
- It does not constitute a formal request for external reassessment.
- It does not override the previous external review.

What the memo does do:

- It records the analytical work done in Sections 3–7.
- It identifies candidate architectural responsibilities in each of the four functions.
- It records the possible overlaps between those candidates.
- It assesses the impact on H-F2 (strengthened candidate basis, not established) and H-F4 (unchanged, untested).
- It states what would be required to move the analysis forward (Sections 8.4 and 9.9).

### 10.4 Final Principle

> **The purpose of this memo is not to establish AetherHuman's independence, but to determine whether the strongest remaining architectural argument survives reduction against the existing dimensions.**
>
> **A credible remainder is necessary for an independence argument, but it is not sufficient to establish an independent architectural dimension.**

The analysis has identified candidate remainders. It has not established that any of them is architecturally distinct. The Phase 4 decision remains (E) Undetermined (interim).

### 10.5 Next Steps

**The immediate next steps are procedural. Any subsequent experimental work remains conditional on the project's authorization requirements.**

1. **Decide whether to submit the memo to the external reviewer.** If yes, a separate formal request is required (Section 9.7).
2. **If submitted, await the reviewer's assessment.** The reviewer's assessment may or may not recommend a change to the Phase 4 decision.
3. **If the reviewer recommends reassessment or a change, process that recommendation according to the project's established decision procedure. Any change to the Phase 4 decision must follow that procedure and must not be inferred from the reviewer's recommendation alone.**
4. **The memo is archived as an internal analytical artifact regardless of whether it is submitted for external review or what the reviewer concludes. Any subsequent review outcome is recorded separately.**
5. **If Phase 5 and Phase 6 are eventually authorized** (via a positive Phase 4 decision), execute the evaluation design (S1–S6) to test H-F4.

### 10.6 Summary

| Element | Status |
|---|---|
| Phase 4 decision | (E) Undetermined (interim) — unchanged |
| Phase 5 | Not authorized |
| Phase 6 | Not authorized |
| H-F2 | Candidate remainders identified; not established |
| H-F4 | Unchanged; untested |
| Memo status | Analytical; not a formal request |
| Next step | Decide whether to submit to external reviewer |

---

**AetherHuman — Stronger Argument Memo for H-F2**
**Version:** 3.0.0
**Status:** Complete
**Decision:** No change to Phase 4 decision (E) Undetermined (interim).
**H-F2:** Candidate remainders identified; not established.
**H-F4:** Unchanged; untested.
**Phase 5 and Phase 6:** Not authorized.
**Author:** Samir Baladi
**Date:** 2026-11-17
© 2026 Samir Baladi — Ronin Institute / Rite of Renaissance
