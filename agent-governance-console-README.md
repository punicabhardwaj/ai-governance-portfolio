# Agent Governance Console

> Prototype 02 · AI Governance Portfolio

A runtime governance dashboard for autonomous AI agents, mapped to the Singapore Model AI Governance Framework for Agentic AI (January 2026) and the NIST AI RMF Manage function.

## Live Demo

Open `agent-governance-console.html` in any browser. No installation required.

Click any agent card to open its detail panel. Inside the panel, click any action row to expand the full decision trace showing exactly why that action was allowed, blocked, or sent for approval.

## Why This Exists

By the end of 2026, an estimated 40% of enterprise applications will embed autonomous AI agents, while only 6% of organizations have advanced AI security strategies for them. Traditional model-level governance does not work for systems that take actions. Singapore launched a dedicated agentic AI governance framework in January 2026 specifically to address this gap.

## What It Does

- **Agent Registry** - every agent with explicit permission scope, accountable owner, autonomy level, and runtime status
- **Decision Traces** - every action shows the policy rule triggered, a step-by-step decision trace, inputs, output, and remediation path if blocked
- **Action Audit Log** - immutable record of every action attempted, with outcomes (Allowed, Blocked, Pending Approval)
- **Incident Register** - significant events with full timelines from detection through resolution
- **Compliance View** - live mapping to Singapore Agentic AI Framework and NIST AI RMF Manage
- **Runtime Controls** - one-click Pause and Kill per agent, with state persisting across the session

## Permission Model

Each agent operates under a three-tier permission model:

| Tier | Meaning |
|---|---|
| **Allowed** | Agent can act autonomously |
| **Blocked** | Denied at the platform layer regardless of agent reasoning |
| **Approval-required** | Technically possible but requires human confirmation before execution |

## Singapore Agentic AI Framework Mapping

| Dimension | Implementation |
|---|---|
| Risk Assessment | Risk tier per agent based on autonomy level, data scope, action authority |
| Human Accountability | Named owner and contact email per agent |
| Technical Controls | Kill switch, permission scoping, purpose binding, immutable audit log |
| End-User Responsibility | Stated purpose on every agent card |

## NIST AI RMF Manage Function Mapping

| Subcategory | Control |
|---|---|
| MANAGE 1.1 | Approval workflow for high-risk actions |
| MANAGE 2.4 | One-click pause and kill |
| MANAGE 4.1 | Continuous action logging and anomaly detection |
| MANAGE 4.3 | Incident lifecycle from detection to resolution |

## Seeded Scenarios

Five agents with realistic governance situations:

| Agent | Key Governance Story |
|---|---|
| Customer Support Triage | Repeated PII access attempts escalated to incident |
| Code Review Assistant | Attempted merge blocked - comment-only by design |
| Sales Outreach Agent | Auto-paused after suspected prompt injection burst |
| Analytics Query Agent | Cost-threshold approval workflow triggered |
| Procurement Drafter | Draft-only - cannot submit POs directly |

## Tech

- Vanilla HTML + React 18 via CDN
- Babel standalone for JSX transpilation
- No backend, no API calls, fully client-side
- Slide-out modal panels with animated transitions

## Honest Limitations

A production version would require real-time event ingestion from agent runtimes, persistent immutable storage, RBAC, webhooks for alerting, and integration with agent platforms (LangChain, CrewAI, OpenAI Assistants). The framework mappings reflect a reasonable interpretation of public guidance, not formal compliance certification.
