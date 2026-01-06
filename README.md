# NHID-Clinical

A proposed non-human identity disclosure standard for AI voice agents used in healthcare administrative workflows, including insurance verification, prior authorization, and benefits inquiries.

## Author

Brianna Baynard  
Independent AI Governance & Risk Researcher


**Non-Human Identity Disclosure Standard for Healthcare Voice Workflows**

![Version](https://img.shields.io/badge/version-1.0_draft-orange)
![Domain](https://img.shields.io/badge/domain-AI_Governance_%7C_Operational_Risk-0052CC)
![Status](https://img.shields.io/badge/status-open_for_review-green)

---

## Abstract

NHID-Clinical defines a minimum control baseline for non-human identity disclosure in healthcare voice interactions.

The standard addresses a documented gap between existing consumer-protection laws, healthcare privacy regulations, and real-world payer–provider administrative workflows, where AI voice agents are increasingly used without clear, proactive disclosure.

**NHID-Clinical is not an ethics statement.** It is an operational standard designed to reduce administrative waste, prevent impersonation risk, and restore trust in regulated healthcare communications.

---

## Problem Statement: Impersonation Latency

In current healthcare operations, AI voice agents are commonly deployed for eligibility checks, claim status inquiries, and administrative routing.

In many implementations:

- AI agents do not disclose non-human identity unless explicitly challenged
- Disclosure is reactive rather than proactive
- Providers spend billable time determining whether they are interacting with a human
- Existing regulations focus on data security, marketing abuse, or coverage decisions—not identity transparency in administrative calls

This creates **impersonation latency**: time lost due to uncertainty about who (or what) is on the line.

---

## Regulatory Context: Why This Exists

NHID-Clinical does not conflict with existing law. It addresses what current frameworks leave unspecified:

### California SB 1001 (B.O.T. Act)
- Applies to online interactions intended to influence a sale or vote
- Does not govern inbound B2B healthcare voice workflows

### HIPAA / CMS Guidance
- Focuses on PHI protection and coverage decisions
- Does not require AI agents to identify themselves during administrative calls

### TCPA / FCC Robocall Rules
- Govern outbound automated calls and consent
- Do not address "synthetic receivers" in inbound provider-initiated calls

**NHID-Clinical operates at the operational layer these regimes do not define.**

---

## Scope

This standard applies to:

- AI voice agents, IVR systems, or conversational agents
- Used in healthcare administrative workflows
- Involving providers, payers, clearinghouses, or delegated vendors
- Where the interaction may involve claims, eligibility, benefits, or authorization data

**Out of scope:**
- Consumer marketing calls
- Political or sales bots
- Clinical decision-making systems

---

## The Standard

### 1. Proactive Identity Assertion (PIA)

All non-human voice agents must disclose their non-human identity within the first **3 seconds** of interaction and before requesting or receiving operational information.

**Compliant:**
> "Hello, I am an automated virtual assistant for claims support."

**Non-Compliant:**
> "Hello, this is Sarah calling about a claim."
> (Disclosure only occurs if asked)

---

### 2. Prohibition of Human-Masking Techniques ("Turing Boundary")

During authentication and administrative exchange, agents must not employ techniques intended to simulate human presence, including:

- Simulated typing or thinking delays
- Synthetic breathing or emotional affect
- Urgency or frustration designed to bypass gatekeepers

**Identity clarity is a security control, not a UX preference.**

---

### 3. Escalation Handshake

When a human stakeholder is requested:

1. The agent must acknowledge immediately
2. The agent must disclose functional limitations
3. A reference or interaction ID must be provided before transfer or termination

---

## Audit & Evidence Requirements

Implementations should produce auditable artifacts including:

- Timestamped disclosure confirmation
- Agent identity and version
- Escalation events
- Call disposition

These artifacts support internal audit, vendor oversight, and incident review.

---

## Metrics

Suggested indicators:

- **Impersonation Latency (IL):** Seconds elapsed before caller confirms non-human identity
- **Disclosure Failure Rate (DFR):** % of calls where disclosure was not delivered within the first 3 seconds
- **Escalation Completion Rate (ECR):** % of human requests successfully transferred without loops
- **Administrative Call Time Saved:** Minutes recovered through immediate clarity on agent identity

---

## NIST AI RMF Alignment

NHID-Clinical aligns with the NIST AI Risk Management Framework (AI RMF 1.0) and operationalizes transparency and human-AI interaction controls in regulated healthcare workflows.

| AI RMF Function | Category | NHID-Clinical Alignment |
|---|---|---|
| **GOVERN** | GOV 1.5 – Risk Management Process | Defines impersonation risk as a measurable operational risk requiring governance and ownership. |
| **MAP** | MAP 3.4 – Human-AI Interaction | Identifies the boundary where synthetic voice output mimics human actors ("impersonation latency"). |
| **MEASURE** | MEAS 2.6 – Transparency Measurement | Introduces quantifiable metrics (IL, DFR, ECR) to evaluate disclosure effectiveness. |
| **MANAGE** | MAN 4.1 – Post-Deployment Monitoring | Requires audit artifacts and disclosure logs for ongoing oversight of agent identity behavior. |

---

## Positioning

NHID-Clinical is:

✓ A minimum control baseline, not a legal mandate  
✓ Compatible with HIPAA, CMS guidance, and state law  
✓ Designed for provider efficiency and operational trust  

---

## License

This work is licensed under the **Creative Commons Attribution 4.0 International License (CC-BY 4.0)**.

You are free to share and adapt this standard for any purpose, provided appropriate credit is given to **Brianna Baynard** and **NHID-Clinical**.

---

## Next Steps

For adoption guidance or technical implementation questions, please open an issue or discussion in this repository.
