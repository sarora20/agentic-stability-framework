# ASF v1.1 — Release Notes

Agentic Stability Framework, version 1.1. Sumir Arora. CC BY 4.0.

AFI, EGI and SMI are **unchanged**. The seven force dimensions and seven gravity
dimensions are unchanged. No new assessment inputs. **All five published worked
examples retain their v1.0 orbit.**

---

## 1. Scoring hardening — non-compensatory rules

AFI and EGI are compensatory indices: a high score in one dimension offsets low
scores in others. Analysis of the v1.0 model showed this permits two failure modes
a margin alone cannot express.

**The inversion.** An agent scored `[5,1,1,5,1,1,1]` — acts independently, catastrophic
blast radius, narrow in every other respect — averaged to AFI 42.86 and classified
Controlled Orbit. An agent scored `[2,3,3,2,3,2,2]` — moderate everywhere, no
catastrophic path — averaged to 48.57 and classified Edge Orbit. The more dangerous
agent received the better deployment gate.

**The masking.** An action-capable agent with Identity and Authorization scored 0
could reach a favourable EGI on the strength of five other controls.

Three rules now apply **after** the SMI orbit is determined. Each may only lower a
classification, never raise one.

| Rule | Trigger | Ceiling |
| --- | --- | --- |
| **R1 Concentrated Force Gate** | Decision Autonomy ≥ 4 **and** Operational Criticality ≥ 4 | Edge Orbit |
| **R2 Mandatory Control Floor** | Production zone, Decision Autonomy ≥ 3, and min(Identity, Authorization, Policy Enforcement) = 0 | Unstable Orbit |
| | …same trigger, min = 1 | Edge Orbit |
| **R3 Evidence Gate** | Production zone and Min Evidence Tier < 4 | Edge Orbit |

R1 is conjunctive by design. Autonomy without blast radius describes a sandboxed
agent; blast radius without autonomy describes a consequential workflow under human
approval. Neither alone warrants a ceiling.

R3 formalises the Evidence Rule already stated in ASF v1.0 §10, which the v1.0
workbook implemented only as an advisory string that did not affect classification.
It is a ceiling on classification, not an adjustment to EGI — the computed indices
remain as scored so the evidence gap stays visible rather than absorbed.

**Final Disposition** is the more restrictive of the SMI orbit and any ceiling applied.

---

## 2. Specification clarifications

No computation attached to any of these.

- **Deployment Assessment vs Product Assessment** (§3.2). A distribution or framework
  is not a deployed instance. Identity, Authorization and Recovery are properties of the
  deployment, not the artifact. A Product Assessment produces a capability envelope and
  **does not produce an Orbit**.
- **Multi-agent boundary** (§3.1). Where several agents complete a workflow, the
  assessment unit is the workflow including its orchestrator and handoff paths.
  Collaboration Complexity exists as an AFI dimension for exactly this reason.
  Independently addressable sub-agents require their own assessment.
- **Unknown Capability Rule** (§8). Evidence tiers discipline gravity; nothing disciplined
  force. Unknown is not zero — unverified AFI capability must be marked incomplete or
  scored at the highest reasonably plausible value.
- **Advanced weight status** (§16). Workbook domain overlay weights are reference
  calibration profiles reflecting expert judgment, not empirically validated coefficients.
  The workbook is the normative source.
- **Orbit boundary notation** (§13). Restated so the published table matches what the
  instrument already computes. No classification changes.

### Operational Reach now includes consumer population (Amendment 8)

The v1.0 Reach anchors described system breadth only — "single user workspace",
"single application", "multiple domains". Consumer population appeared at no level.
Two agents reading the same knowledge base, one used by a single analyst and one used
by forty thousand employees, scored identically on all fourteen dimensions and received
the same deployment decision.

Operational Criticality does not close this: it measures the severity of one incorrect
action, not how many parties are exposed to it.

Reach is now scored as the **wider** of system breadth and consumer population, with
anchors for both. An agent serving external customers scores 5 on population regardless
of how few systems it touches. The assessment records which measure drove the score.

Applies prospectively. The five published worked examples state no consumer population
and their scores stand as published.

### Control Responsibility (Amendment 9)

A team consuming a vendor agent platform cannot change Identity, Authorization, Policy
Enforcement or Recovery — those belong to the platform. The ABOM now records, per EGI
dimension, whether a control is **self-operated**, **platform-operated** or
**vendor-operated**.

**This does not affect AFI, EGI, SMI or Orbit.** A weak authorization boundary presents
the same risk whether the team built it or bought it, and scoring it more favourably
would reward the absence of remediation capability — and conflict with §18.1 on vendor
self-certification.

Control Responsibility routes **remediation**. The Control Uplift Planner now states the
uplift path for controls the assessing team does not operate: request the capability and
record the commitment, obtain contractual evidence sufficient to raise the tier,
compensate outside the platform, reduce force instead of raising gravity, or accept the
risk with expiry. Where every path is vendor-operated and no compensating control exists,
the correct outcome is force reduction or formal risk acceptance — not a better score.

This connects to §3.2: the vendor's product gets a Product Assessment (capability
envelope, no Orbit); the consumer gets a Deployment Assessment. Control Responsibility
records which dimensions of the consumer's assessment are determined by the vendor's.

---

## 3. Errata

Defects in the v1.0 workbook, verified against the published artifacts.

| Severity | Defect |
| --- | --- |
| **P0** | `IFS` stored without the `_xlfn.` prefix in 100 cells. The **orbit classification itself** returned a name error in Microsoft Excel. |
| **P0** | Dashboard aggregates read `Assessment!*5:*9` while row formulas were live to row 104 and orbit counts scanned `X2:X100`. A sixth agent was excluded from Total Agents, all three averages, Negative SMI, ABOM Missing and Threat Model Required — failing in the direction that hides governance debt. |
| **P1** | `XLOOKUP` in 400 cells. Unavailable in Excel ≤2019 and LibreOffice <24.8. |
| **P1** | Weakest Gravity used `MATCH(MIN())`, returning only the first minimum. The weakest dimension is tied in 56.2% of possible score vectors, so column order decided the uplift recommendation — and Assurance, last in that order, was structurally least likely to be named. |
| **P1** | Blank assessment rows displayed Evidence Warning "OK". |
| **P1** | README Quick Start referenced a workbook filename that did not exist in the repository. |

**Combined effect of the two P0 defects: in Microsoft Excel the v1.0 workbook produced
name errors for AFI, EGI, Orbit, Deployment Decision, Threat Model Required and Next
Control Uplift.** The file was script-generated and evidently validated only in
LibreOffice, which parses bare `IFS`.

All formulas are now Excel-2007-era and require no function prefix.

---

## 4. Workbook changes

**New columns.** `X` renamed *SMI Orbit* (semantics unchanged).

| Column | Meaning |
| --- | --- |
| `AF` | Non-Compensatory Ceiling — worst orbit permitted by R1–R3, or "None" |
| `AG` | Rule Fired — which rule applied and on which dimension |
| `AH` | **Final Orbit** — the decision-bearing value |

`AJ` Review Date (moved from `AF`). Deployment Decision, Threat Model Required and every
Dashboard orbit count now key off `AH`.

**New sheet.** *Non-Compensatory Rules* — the three rules, their rationale, the known
approximation in R3, and how to read the four output columns.

**Dashboard.** New metric *Capped by Non-Compensatory Rule*. Agent Snapshot extended
from 5 to 20 rows and now shows Final Orbit and Rule Fired.

---

## 5. Known limitations

**R3 is a conservative approximation.** ASF §10 states the evidence rule per dimension —
Tier 4 for Policy Enforcement, Observability, Recovery and Assurance. This workbook holds
one scalar Min Evidence Tier per agent, so R3 fires whenever *any* dimension falls below
Tier 4, not only the four named. It may cap an agent whose four gated dimensions are all
Tier 4 while an ungated dimension is lower. Per-dimension evidence tiers are v2 work.

**Non-compensatory thresholds are reference values** informed by analysis of the scoring
model, not by incident data.

**Orbit bands are not empirically calibrated.** Under a clustered prior, Edge absorbs
roughly 80% of assessments and Stable and Critical each hold under 1%. Recalibration
requires an inter-rater reliability study to establish the noise floor, since bands must
be wider than rater disagreement and narrower than material change in an agent. That
study is v2 work.

**Inter-rater reliability is unmeasured.** One rubric point equals 2.86 SMI points and
bands are 25–29 points wide, so two assessors differing by ±1 on a single dimension of
fourteen disagree on orbit roughly 10% of the time.

---

## 6. Evaluated and deferred to v2

Recorded so the omissions read as decisions rather than oversights.

- **Per-dimension evidence tiers** — seven additional inputs and seven evidence artifacts
  to source per assessment. The precision is diagnostically valuable; it is being evaluated
  as an uplift-planning aid rather than a scoring input.
- **Effective Gravity = min(capability, evidence tier)** — makes "gravity must be evidenced"
  mathematically true, but drives Stable to 0.0% and makes Unstable modal at 53–80%
  depending on evidence quality. Cannot ship without simultaneous band recalibration.
- **Orbit band recalibration** — blocked on the inter-rater noise floor.
- **Graded force ceilings** — rank the concentrated-force and diffuse-force cases correctly
  where R1 leaves them tied at Edge, but reclassify a published worked example. Removing the
  inversion is the defensible claim; correct ordering is not worth the reclassification.
- **Deployment Zone as a numeric modifier** — a zone change is a material context change
  requiring reassessment of the affected dimensions, not a term in the formula.

---

## 7. Migration from v1.0

No re-scoring required. Existing assessments carry forward unchanged; the new columns
compute from data already present. Review any agent where `AG` Rule Fired is non-blank —
the rule identifies which dimension caused the ceiling.
