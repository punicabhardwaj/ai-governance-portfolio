# AI Use Case Intake & Risk Classifier

> Prototype 01 · AI Governance Portfolio

A structured intake and risk classification tool for product teams submitting AI systems for governance review. Generates a deterministic governance assessment mapped to NIST AI RMF and the EU AI Act.

## Live Demo

Open `ai-governance-hub.html` in any browser. No installation required.

Use the **Quick Demo** buttons to pre-load three example scenarios:
- **Low Risk** - Internal engineering code search
- **High Risk** - Customer churn prediction model
- **Critical Risk** - Automated resume screener (EU AI Act Annex III)

## What It Does

1. Walks a product team through a 4-step intake form covering use case basics, data & privacy, impact assessment, and deployment readiness
2. Runs a deterministic rule engine that scores residual risk across 20 weighted factors
3. Returns a full governance assessment including risk level, NIST AI RMF tier, EU AI Act classification, key risks, recommended controls, and an approval decision
4. Generates a printable PDF governance memo via the Download Report button

## Why a Rule Engine, Not an LLM

Real governance tools (OneTrust, Credo AI, Holistic AI) classify AI risk using deterministic rules, not generative models. Rule-based classification is auditable, repeatable, and defensible to regulators. Every decision in this tool can be traced to a specific rule and input value.

## Framework Mapping

### NIST AI RMF 1.0 - Implementation Tiers

Tier is determined by the number of governance controls present:

| Controls in Place | Tier |
|---|---|
| 4 (monitoring + explainability + rollback + consent) | Tier 4 - Adaptive |
| 3 | Tier 3 - Repeatable |
| 2 | Tier 2 - Risk Informed |
| 0-1 | Tier 1 - Partial |

### EU AI Act (Regulation EU 2024/1689)

| Trigger | Classification | Reference |
|---|---|---|
| Fully automated decision + high harm or sensitive data | High Risk | Article 6 + Annex III |
| Automated decisions or sensitive data alone | High Risk | Annex III |
| Customer-facing generative AI | Limited Risk | Article 50 |
| Sandbox / research / minimal scale | Minimal Risk | Recital 165 |
| Default | Limited Risk | Article 50 |

## Risk Scoring Rubric

| Factor | Score |
|---|---|
| Sensitive data categories | +3 |
| High potential harm | +3 |
| Fully automated decisions | +3 |
| PII processing | +2 |
| Scale > 1M people | +2 |
| Customer-facing production | +2 |
| Black-box / unexplainable | +2 |
| No model monitoring | +2 |
| Autonomous agent | +2 |
| No documented data consent | +2 |
| Other partial / uncertain factors | +1 each |

**Thresholds:** Critical (14+) · High (9-13) · Medium (5-8) · Low (0-4)

## Approval Logic

| Condition | Decision |
|---|---|
| Critical risk OR EU High Risk | Escalate to AI Review Board |
| High risk | Conditional Approval (90-day review) |
| Medium risk | Conditional Approval (self-attestation) |
| Low risk | Approved |

## Tech

- Vanilla HTML + React 18 via CDN
- Babel standalone for JSX transpilation
- No backend, no API calls, no dependencies to install
- Runs entirely in the browser

## Honest Limitations

A production version would require persistent storage, authentication, GRC integration, versioned rule sets, and SLA tracking. The rules reflect a reasonable interpretation of public framework guidance, not formal legal advice.
