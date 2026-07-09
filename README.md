# Agentic Stability Framework (ASF)

**A force-based enterprise architecture framework for governing autonomous AI systems.**

[![DOI](https://img.shields.io/badge/DOI-10.5281%2Fzenodo.21281297-blue)](https://doi.org/10.5281/zenodo.21281297)
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey)](https://creativecommons.org/licenses/by/4.0/)
![Version](https://img.shields.io/badge/version-v1.0-informational)

> Repo links below point to https://github.com/sarora20/agentic-stability-framework

---

## The thesis

**Agentic maturity is not the ability to increase autonomy. It is the ability to increase autonomy while maintaining stability.**

Enterprises are moving from assistive AI to agentic AI. A chatbot that gives a wrong answer creates a quality problem. An agent that deploys the wrong workload, grants the wrong access, updates the wrong customer record, or triggers the wrong financial workflow creates an **operational stability problem**.

The hard part is that agent capability expands quickly while governance expands slowly. Adding a tool, an MCP server, a memory store, or an approval delegation each feels incremental — but collectively they can push autonomy beyond the enterprise's ability to observe, constrain, audit, and recover.

ASF gives enterprise architects a repeatable way to answer one question, per agent, in context: **is the governance around this agent strong enough to justify the autonomy we're giving it?**

---

## The model in one screen

ASF measures two opposing forces for a single **agentic system instance** (the deployed configuration — model, prompts, runtime, memory, tools, MCP servers, identity, permissions, policies, and operating context) and reports the margin between them.

| Index | Measures | Question it answers |
|---|---|---|
| **AFI** — Agentic Force Index | Operational pressure the agent creates | How much force does this agent create? |
| **EGI** — Enterprise Gravity Index | Governance and control strength around it | How much control exists around this agent? |
| **SMI** — Stability Margin Index | `SMI = EGI − AFI` | Is governance proportional to autonomy? |

SMI places the agent in an **orbit**, which maps to a default deployment decision:

| SMI | Orbit | Default decision |
|---|---|---|
| +40 to +100 | **Stable** | Approved for scale with monitoring |
| +15 to +39 | **Controlled** | Approved with standard controls |
| −14 to +14 | **Edge** | Pilot / limited production; active control management |
| −15 to −39 | **Unstable** | Do not expand; control uplift required |
| −40 to −100 | **Critical** | Do not deploy without formal exception |

AFI and EGI each score seven dimensions (0–5). EGI scores are **evidence-tiered** (0 = claimed, 5 = continuously audited), so a control only counts if it can be shown to work at runtime — not just on a slide.

> SMI is a directional architecture indicator, not a probability of failure or a proof of safety. See *Limitations* below.

---

## What's in this repo

| File | What it is |
|---|---|
| `ASF_Whitepaper_v1_0_Initial_Public_Release.pdf` | The full specification and whitepaper |
| `ASF_Assessment_Workbook_v1_0_Initial_Public_Release.xlsx` | The working assessment tool — score an agent end to end |
| `LICENSE` | Creative Commons Attribution 4.0 International |

---

## Quick start

1. **Download the workbook** (`ASF_Assessment_Workbook_v1_0.xlsx`) and open it.
2. **Pick one agent** in one business context. ASF scores an agentic system instance, not your whole enterprise.
3. **Fill the ABOM** (Agent Bill of Materials) tab — model, tools, MCP servers, data, identity, permissions, action authority. This defines the assessment boundary.
4. **Score AFI and EGI** using the rubric tabs. For EGI, record the evidence tier behind each score.
5. **Read the SMI and orbit** off the dashboard, then follow the deployment gate and, if the margin is thin or negative, the **Control Uplift Planner**.

A full assessment produces an agent-level stability profile, a deployment recommendation, and a prioritized control-uplift plan — usable directly in an architecture review board.

---

## What ASF is — and is not

**ASF is:**
- An enterprise architecture assessment model for agentic AI, applied one agentic system instance at a time.
- A way to compare autonomous capability against governance strength and surface **governance debt**.
- A complement to AI risk, security, compliance, and management-system frameworks.

**ASF is not:**
- A replacement for NIST AI RMF, ISO/IEC 42001, OWASP guidance, or Zero Trust.
- A complete security threat model or a regulatory compliance certification.
- A mathematical proof that an agent is safe.
- A maturity score for the entire enterprise.

ASF sits *one layer beneath* organization-level AI governance frameworks — as the agent-level architecture measurement they assume but do not themselves provide. It aligns with **NIST AI RMF**, **ISO/IEC 42001**, **OWASP Top 10 for Agentic Applications / Multi-Agent Threat Modeling**, **Zero Trust**, and **OPA/Cedar-style policy**.

---

## Who it's for

CIOs, CISOs, CTOs, enterprise architects, platform teams, and AI governance boards standing up or reviewing production agent deployments.

---

## Status and limitations

This is **v1.0**, released openly for practitioner adoption and field feedback. It is a decision-support framework, not a validated measurement instrument. Known limits, stated plainly:

- **Scoring is judgment-based.** Two qualified assessors can score the same agent differently. Calibration sessions and evidence-tier requirements reduce, but do not eliminate, variance.
- **Orbit thresholds are heuristic** starting points, not empirically derived safety boundaries. Calibrate them against your own incident history and risk appetite.
- **A positive SMI indicates proportional governance under the model — not guaranteed safe behavior.** Use ASF alongside threat modeling, security testing, runtime monitoring, and regulatory review.

The framework improves through use. If you apply it and something breaks, is unclear, or is wrong, that feedback is the point.

---

## Contributing and feedback

Open an [issue](https://github.com/sarora20/agentic-stability-framework/issues) to report where the framework is unclear, where a rubric anchor is wrong, or where a domain overlay is missing. Real-world assessments — including anonymized ones that land in surprising orbits — are especially useful for calibrating thresholds in future versions.

---

## Citation

If you use or reference ASF, please cite it:

> Arora, Sumir. *Agentic Stability Framework: A Force-Based Enterprise Architecture Framework for Autonomous AI Systems.* v1.0 Initial Public Release, 2026. https://doi.org/10.5281/zenodo.21281297

```bibtex
@techreport{arora2026asf,
  author  = {Arora, Sumir},
  title   = {Agentic Stability Framework: A Force-Based Enterprise
             Architecture Framework for Autonomous AI Systems},
  year    = {2026},
  version = {v1.0},
  note    = {Initial Public Release},
  doi     = {10.5281/zenodo.21281297},
  url     = {https://doi.org/10.5281/zenodo.21281297}
}
```

---

## License

© 2026 Sumir Arora. Licensed under the [Creative Commons Attribution 4.0 International License (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/). You may share and adapt this work, including commercially, with attribution.
