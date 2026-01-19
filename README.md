> [!IMPORTANT]
> **🚧 v1.2 Drafting in Progress**
> We are currently resolving architectural gaps identified in v1.1, including SIP Header Identity, Failover Logging, and Bot-to-Bot Deadlocks.
> [**View the v1.2 Working Draft**](v1.2-draft.md) to see the proposed technical specifications.

# NHID-Clinical v1.1

**Non-Human Identity Disclosure Standard for Healthcare Voice Workflows**

[![Version](https://img.shields.io/badge/version-1.1_candidate-blue)](https://github.com/thankcheeses/NHID-Clinical)
[![Domain](https://img.shields.io/badge/domain-AI_Governance_%7C_Operational_Risk-0052CC)](https://github.com/thankcheeses/NHID-Clinical)
[![Status](https://img.shields.io/badge/status-open_for_comment-green)](https://github.com/thankcheeses/NHID-Clinical)

---

## Abstract

**NHID-Clinical** defines a minimum control baseline for non-human identity disclosure in B2B healthcare voice interactions.

The standard addresses a documented gap between existing consumer-protection laws, healthcare privacy regulations, and real-world payer–provider administrative workflows. It specifically targets **"Impersonation Latency"**—the operational waste and security risk caused when a human provider cannot immediately distinguish an AI agent from a human counterpart.

**Note:** This standard is scoped strictly for **B2B Administrative Workflows** (Provider-to-Payer, Business Associate-to-Payer). It does not currently cover direct-to-consumer or patient-facing clinical triage.

---

## Problem Statement

In current healthcare operations, AI voice agents are commonly deployed for eligibility checks, claim status inquiries, and administrative routing. In many implementations:

* AI agents do not disclose non-human identity unless explicitly challenged.
* Disclosure is reactive rather than proactive.
* Providers spend billable time determining whether they are interacting with a human.

This creates **Impersonation Latency**: time lost due to uncertainty about the nature of the counterparty.

---

## Positioning

NHID-Clinical is a voluntary governance standard that operationalizes transparency requirements.

* **Beyond Minimums:** It aligns with the *intent* of HIPAA (access control), NIST (measurability), and the California B.O.T. Act (disclosure timing), while establishing strict operational boundaries that may exceed baseline legal requirements.
* **Operational Focus:** Unlike broad ethical frameworks, it provides binary, testable logic gates (e.g., "Pre-Data Exchange") for engineering and QA teams.
* **Risk Reduction:** Designed to reduce "Impersonation Latency"—a specific operational risk not fully addressed by general privacy laws.

---

## Regulatory Context & Compatibility

NHID-Clinical operates at the **operational layer**, complementing existing legal frameworks without conflict:

* **HIPAA:** NHID-Clinical focuses on the *identity* of the actor, ensuring that the "Minimum Necessary" standard is applied to the correct entity type (human vs. machine).
* **TCPA / FCC:** While these govern outbound consent, NHID-Clinical manages the *content* of the inbound handshake to prevent deceptive practices in exempt B2B calls.
* **California B.O.T. Act:** Extends the spirit of disclosure to private healthcare administrative channels not explicitly covered by public-facing consumer laws.

---

## The Standard

### 1. Proactive Identity Assertion (PIA)

**The Rule:**
All non-human voice agents must proactively disclose their non-human identity **during the initial greeting** and **prior to the solicitation or intake of any operational data** (e.g., NPI, Member ID, Claim Number).

**Timing & Latency:**
Disclosure must occur **before any request for operational data exchange**. This "Pre-Data Exchange" requirement accounts for VoIP/SIP latency and variable greeting lengths while maintaining a clear, auditable boundary.

**Compliant Example:**
> "Hello, I am an automated assistant for [Payer Name] Claims. I can help you with status and eligibility. To begin, please say the NPI."

**Non-Compliant Example:**
> "Hello, this is Sarah. Can I get the NPI?"
> *(Violation: Uses a human name without qualification; requests data before disclosure.)*

---

### 2. Prohibition of Deceptive Artifacts ("The Turing Boundary")

**The Rule:**
Agents must not employ synthetic audio artifacts that serve no communicative function other than to imply biological presence or mask processing latency.

**Prohibited "Masking" Techniques:**
* **Simulated Physical Actions:** Sound effects of keyboard typing, mouse clicking, or paper shuffling.
* **Simulated Biological Functions:** Synthetic breathing sounds, clearing of the throat, or coughing.
* **Deceptive Latency Masking:** Using scripted "thinking" sounds (e.g., "Umm...", "Let me see...") implies a human cognitive process. Agents should instead use functional status updates (e.g., "One moment while I search that record...").

*Note: Natural prosody, inflection, and conversational pacing required for clear communication are **permitted** and encouraged.*

---

### 3. Escalation & Safe Failover

**The Rule:**
When a human stakeholder explicitly requests a transfer or indicates the agent is failing to understand:

1.  **Acknowledgement:** The agent must immediately acknowledge the request (e.g., "I understand you need to speak to a specialist").
2.  **Context Preservation:** The agent should generate a reference number or interaction ID to prevent data reentry.
3.  **Safe Failover:**
    * *If human staff is available:* Transfer immediately.
    * *If human staff is unavailable (e.g., after hours):* The agent must explicitly state hours of operation and offer a voicemail or callback option rather than looping or disconnecting.

---

## Audit & Evidence Requirements

To ensure compliance without imposing undue technical burdens, implementations must maintain **Interaction Logs**.

**Minimum Required Evidence (Tier 1):**
* **Transaction Log:** A text-based log entry timestamping the "Identity Assertion" event relative to the "Call Connected" event.
* **Script Versioning:** Documentation of the active call script proving the disclosure verbiage was present in the production flow.

**Recommended Evidence (Tier 2):**
* **Audio Artifact:** A recording of the first 30 seconds of the interaction (subject to organizational data retention policies).

---

## Metrics

Suggested indicators for measuring success:

* **Disclosure Failure Rate (DFR):** % of calls where data exchange was attempted *before* identity disclosure.
* **Escalation Loop Count:** Frequency of callers repeating "Agent" or "Representative" more than twice (indicating failed escalation logic).
* **Administrative Velocity:** Reduction in total call handle time (AHT) due to the elimination of "Are you a robot?" verification loops.

---

## NIST AI RMF Alignment

NHID-Clinical operationalizes the **NIST AI Risk Management Framework (AI RMF 1.0)**:

| AI RMF Function | Category | NHID-Clinical Alignment |
| :--- | :--- | :--- |
| **GOVERN** | GOV 1.5 – Risk Management | Defines "impersonation" as a specific operational risk to be governed. |
| **MAP** | MAP 3.4 – Human-AI Interaction | Establishes the boundary where synthetic voice output must not deceive human actors. |
| **MEASURE** | MEAS 2.6 – Transparency | Introduces quantifiable metrics (DFR) to evaluate disclosure effectiveness. |
| **MANAGE** | MAN 4.1 – Post-Deployment Monitoring | Requires audit artifacts and disclosure logs for ongoing oversight of agent identity behavior. |

---

## Known Gaps & Future Scope

This v1.1 candidate does not currently address:

* **Patient-facing workflows:** Direct-to-consumer or clinical triage interactions.
* **Outbound calls:** Payer-initiated or proactive agent calls.
* **International compliance:** GDPR or non-U.S. regulatory contexts.
* **Accessibility:** Multilingual support, deaf/hard-of-hearing accommodations, or cultural communication variations.
* **Multi-entity integrations:** Scenarios where AI handles data across multiple payers or vendors dynamically.
* **Enforcement mechanisms:** Certification, audit standards, or adoption incentives.

These are candidates for v1.2 and beyond, contingent on community feedback.

---
## v1.2 Roadmap

Based on community feedback, the following gaps have been identified for v1.2:

| Issue | Category | Priority | Impact |
|---|---|---|---|
| Bot-to-Bot Standoff | Architecture | High | Blocks B2B automation scaling |
| Technical Signaling | Optimization | Medium | Improves efficiency, reduces latency |
| Interrupt/Barge-In | Operational | High | Common failure mode in practice |
| Context Preservation | Operational | Medium | Affects escalation viability |
| Failover Liability | Compliance | High | Legal/claims risk if unaddressed |

**Recommended Release Schedule:** Q2 2026 (after 30–60 days of feedback collection on v1.1)

**Track Progress:** [View v1.2 Issues](https://github.com/thankcheeses/NHID-Clinical/issues)


## License

This work is licensed under the **Creative Commons Attribution 4.0 International License (CC-BY 4.0)**.

**Author:** Brianna Baynard  
**Repository:** [github.com/thankcheeses/NHID-Clinical](https://github.com/thankcheeses/NHID-Clinical)

---

## Feedback & Next Steps

This is a **v1.1 Candidate** released for public comment. We invite:

* **Technical feedback** on the Pre-Data Exchange requirement and audit logging feasibility.
* **Compliance input** from HIPAA officers, healthcare IT architects, and payer/provider operations teams.
* **Implementation experience** from organizations piloting similar controls.

Please open an issue or discussion in this repository to contribute.

---

## Changelog

**v1.1 (Candidate)**
* Shifted timing requirement from "3-second window" to "Pre-Data Exchange gate" for improved auditability and latency-agnostic compliance.
* Added "Known Gaps & Future Scope" section for transparency about coverage limitations.
* Refined positioning language to emphasize governance best practice over regulatory equivalence.
* Clarified distinction between permitted natural prosody and prohibited deceptive artifacts.

**v1.0**
* Initial draft with temporal disclosure requirements and NIST/HIPAA alignment mapping.
