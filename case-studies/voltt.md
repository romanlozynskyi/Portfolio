# Voltt

**Category:** Product Rebuild / Startup Platform  
**Status:** In progress  
**Source code:** Private  
**Role:** Co-founder and partner on the rebuild: product architecture, data model, AI boundaries, workflows, permissions, integrations, and production design.  
**Problem:** The current version reflects short-term prototype decisions, so the rebuild starts from architecture to support product growth.  
**Result:** Rebuild in progress, with the early diagnostic dashboard implemented and the core product architecture defined and under implementation.  

## Overview

Voltt is an architecture-first AI SaaS platform for startup diagnostics, decision support, and execution workflows, being rebuilt from a short-term implementation into a scalable product architecture.

It is for startup teams that assess their readiness and decide what to do next. As co-founder and partner on the rebuild, I own the product architecture, data model, AI boundaries, workflows, permissions, integrations, and production design.

- Architecture first: a shared User, Project, and Entitlements foundation instead of isolated product silos
- Deterministic diagnostics, with AI limited to explaining and evaluating
- Core and Sprint flows, with evidence-based progression
- Payments, async jobs, analytics, and observability designed in from the start

![Startup diagnostic dashboard](../assets/voltt/cover/dashboard.jpg)

## Product outcomes & evidence

No traction or metrics are claimed, and planned work is not presented as shipped. The evidence is grouped by status.

- Implemented: an early diagnostic dashboard with an overall startup score, diagnostic dimensions, top red flags, a 7/30/90-day roadmap, priority next actions, an evidence tracker, and an AI coach panel. It is shown with demo data.
- Architected and defined: the startup diagnostic workflow, structured project context (Project Facts), deterministic diagnostics and scoring, the 7/30/90 roadmap logic, a shared account and project architecture, the Core and Sprint flows, and production acceptance requirements.
- Planned: the rest of the rebuild, including payments and entitlements, async jobs and report generation, and production acceptance testing, none of which is presented as shipped.

## Key product & engineering decisions

- Deterministic truth, AI interpretation: scoring, rules, red flags, and recommendations come from a deterministic rule engine, and AI explains and evaluates but does not set the truth.
- AI cannot change state: AI cannot directly change payment state, access, scoring truth, or progression.
- One shared foundation: a shared User, Project, and Entitlements architecture serves every product flow instead of isolated product silos.
- Everything versioned: prompts, models, schemas, rubrics, methodology, and policies are versioned, so a result can be traced to what produced it.
- Evidence-based progression: progress depends on evidence, with human review gates and explicit escalation and failure paths.

## System & architecture

`Next.js` `TypeScript` `Supabase` `PostgreSQL` `OpenAI API` `Vercel`

The core product logic runs in one direction: Answer -> Score -> Dimension -> Rule Engine -> Red Flag -> Recommendation -> Next Action -> Evidence Requirement -> AI explanation. Everything up to the AI explanation is deterministic and rule-based, and the AI explanation comes last and cannot change what came before it.

The confirmed architecture for the rebuild is organized like this:

- Application and account layer: Next.js, TypeScript, and Tailwind on Vercel, with Supabase Auth for accounts and a shared User, Project, and Entitlements model.
- Data model and RLS: Supabase and PostgreSQL with row-level security, and Supabase Storage for files.
- Deterministic diagnostic and rule engine: scores, dimensions, red flags, recommendations, and next actions computed by rules.
- AI gateway and structured outputs: the OpenAI API is called only through a server-side AI gateway, with structured outputs checked against a schema.
- Payments and entitlements: WayForPay for payments, with entitlements deciding access.
- Async jobs and report generation: async background jobs, HTML-to-PDF reports, and Resend for email.
- Analytics and observability: PostHog for product analytics and Sentry for error monitoring.
- Versioning and auditability: versioned prompts, models, schemas, rubrics, methodology, and policies, with an audit trail.

## Validation & production quality

No acceptance-test results are claimed. These controls are labeled as designed or required until they are verified in the running product.

- Idempotent payment and webhook handling: required, so a repeated webhook or a duplicate payment cannot grant access twice.
- Authorization and RLS boundaries: designed, so access is enforced in the database through row-level security as well as in the application.
- AI schema validation: required, so an AI output must pass its schema before it is used.
- No AI-driven access or payment: designed, so AI cannot directly unlock access or confirm a payment.
- Retries and manual fallback: required for async jobs and AI calls, with a manual path when they fail.
- Auditability: designed, so versioned prompts, models, and policies make results traceable.
- Duplicate protection: required against duplicate submissions and duplicate payments.
- Evidence validation and human escalation: designed, so evidence is validated and ambiguous cases escalate to human review.

## Outcome

Voltt is in active rebuild and implementation, not a completed production system. The early diagnostic dashboard and the core architecture are in place, and the rest is defined and still being implemented.

Capabilities demonstrated:

- Architecture-first product engineering
- AI with deterministic boundaries
- Multi-product SaaS architecture on one shared foundation
- Secure data and access design, with payments and entitlements
- Human-in-the-loop and production-readiness thinking

## Public portfolio note

The dashboard screenshot shows demo data. Voltt is under active rebuild, so the features and architecture described here are labeled by their status.
