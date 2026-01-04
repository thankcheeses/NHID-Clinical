# NHID-Clinical — NIST AI RMF Mapping (Detailed)

This document provides a detailed mapping between the NHID-Clinical standard
and the NIST AI Risk Management Framework (AI RMF 1.0).

The purpose of this mapping is to demonstrate how NHID-Clinical operationalizes
existing NIST AI RMF concepts for a specific, under-defined risk domain:
non-human identity disclosure in healthcare voice workflows.

This document is informational and does not claim formal endorsement by NIST.

---

## Overview

NHID-Clinical primarily aligns with the following NIST AI RMF characteristics:

- Transparency
- Human-AI Interaction
- Accountability
- Post-deployment Monitoring

The standard focuses on **operational controls**, not model development,
training data, or clinical decision logic.

---

## GOVERN Function

### GOV 1.5 — Risk Management Processes Are Established

**NIST Intent:**  
Organizations should define and govern AI-related risks through documented,
repeatable processes.

**NHID-Clinical Alignment:**  
- Defines *impersonation risk* as a distinct operational risk class
- Introduces "impersonation latency" as a measurable risk indicator
- Requires ownership of disclosure behavior as a governance responsibility

**Relevant NHID-Clinical Controls:**  
- Proactive Identity Assertion (PIA)
- Disclosure Failure Rate (DFR) metric

**Operational Interpretation:**  
Identity ambiguity is treated as a governable risk, not a UX decision.

---

## MAP Function

### MAP 3.4 — Human-AI Interaction Context Is Characterized

**NIST Intent:**  
Organizations should understand how humans interact with AI systems and where
misunderstanding or misuse may occur.

**NHID-Clinical Alignment:**  
- Identifies the boundary where synthetic voice output mimics human actors
- Explicitly maps the moment of interaction where identity ambiguity occurs
- Defines the administrative call as a high-risk interaction surface

**Relevant NHID-Clinical Controls:**  
- Time-bound identity disclosure
- Scope definition for administrative workflows

**Operational Interpretation:**  
The standard maps *when* identity confusion happens, not just *that* it happens.

---

## MEASURE Function

### MEAS 2.6 — Transparency Is Measured and Evaluated

**NIST Intent:**  
Organizations should assess whether AI system behaviors are transparent and
understandable to affected stakeholders.

**NHID-Clinical Alignment:**  
- Introduces measurable indicators for disclosure behavior
- Moves transparency from qualitative to quantitative evaluation

**NHID-Clinical Metrics:**  
- Impersonation Latency (IL)
- Disclosure Failure Rate (DFR)
- Escalation Completion Rate (ECR)

**Operational Interpretation:**  
Transparency is evaluated using system evidence, not user perception alone.

---

## MANAGE Function

### MAN 4.1 — Post-Deployment Monitoring Is Performed

**NIST Intent:**  
AI systems should be monitored after deployment to detect emergent risks and
control failures.

**NHID-Clinical Alignment:**  
- Requires audit artifacts for identity disclosure behavior
- Enables detection of drift toward deceptive or ambiguous interaction patterns
- Supports vendor oversight and SLA enforcement

**Relevant NHID-Clinical Controls:**  
- Disclosure event logging
- Escalation tracking
- Agent identity/version tracking

**Operational Interpretation:**  
Disclosure behavior is continuously monitored, not assumed to remain compliant.

---

## Out-of-Scope NIST Areas

NHID-Clinical intentionally does not address:

- Model training data governance
- Bias or fairness in decision outputs
- Clinical decision-making systems
- Explainability of automated decisions

These areas are assumed to be governed by complementary standards or controls.

---

## Summary

NHID-Clinical does not redefine NIST AI RMF principles.
It operationalizes them for a narrowly scoped, high-friction risk domain
that is not explicitly addressed in existing guidance.

This mapping demonstrates that NHID-Clinical:
- Fits within established federal risk frameworks
- Can be adopted without conflicting with broader AI governance programs
- Extends NIST AI RMF concepts into real-world healthcare operations
