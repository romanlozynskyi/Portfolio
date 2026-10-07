# AstuteWheel

**Category:** Production SaaS / CRM / Financial Planning  
**Status:** Live  
**Live:** https://www.astutewheel.com.au/  
**Badge:** Financial SaaS  
**Source code:** Private  
**Role:** Senior Product Engineer responsible for evolving the product across architecture, data, permissions, financial workflows, integrations, automation, AI features, and production delivery.  
**Problem:** A mature financial-planning SaaS and CRM had to keep evolving while preserving complex customer workflows, financial logic, data integrity, integrations, and production reliability.  
**Result:** A mature production financial platform serving 120k+ active users across financial planning, CRM, reporting, payments, documents, integrations, and automation.  
**Metric:** 120k+ | active users | product  
**Metric:** 10+ | production integrations | evidence | Payments, documents, email, spreadsheets, workflow automation, and AI  

## Overview

AstuteWheel is a mature financial-planning SaaS and CRM platform serving 120k+ active users across financial planning, CRM, reporting, payments, documents, integrations, and automation.

It runs on Next.js, TypeScript, Supabase, and PostgreSQL. My work spans architecture, data, permissions, workflows, integrations, AI features, and production delivery.

![AstuteWheel Scope of Advice](../assets/astutewheel/cover/scope-of-advice.png)

## Problem & users

The platform serves financial advice practices: client engagement, advice delivery, and practice management run on one system. A product at this stage cannot be paused or rebuilt from scratch, so it has to keep evolving while customers keep working:

- Complex customer workflows and financial logic must keep behaving the same way.
- Data integrity and permissions must hold across CRM, reporting, payments, and documents.
- New functionality has to fit established workflows instead of disrupting them.

![Client wellbeing and financial planning](../assets/astutewheel/screenshots/wellbeing.png)

## My role & ownership

I am the Senior Product Engineer responsible for evolving the product. The areas I own:

- Product architecture and the relational data model
- Permissions and data integrity
- Financial workflows, CRM operations, and reporting
- Integrations and automation across payments, documents, email, spreadsheets, and workflow tools
- AI-enabled features built on OpenAI/ChatGPT
- Production delivery, reliability, and troubleshooting

![Dashboard](../assets/astutewheel/screenshots/dashboard.png)
![Client and operational workflows](../assets/astutewheel/screenshots/clients.png)

## Product outcomes & evidence

Outcomes for the product, and the engineering evidence behind them.

AstuteWheel is a live, mature financial-planning SaaS and CRM with connected workflows across financial planning, CRM, reporting, payments, documents, and automation. Production permissions, relational data, reporting, automation, and troubleshooting are part of everyday delivery, and the stack and integrations behind them are described under System & architecture.

## Product decisions

- Evolve, do not rewrite: improvements ship inside the live system without disrupting existing users, so each change is judged by what it could break as well as what it adds.
- Established workflows first: new functionality is balanced against the workflows customers already depend on.
- Data integrity and permissions by design: a relational data model and explicit permission rules keep CRM, reporting, and financial data consistent.
- One source of business logic: duplicate logic across workflows and integrations is avoided, so behavior stays predictable.
- Integrations chosen for the job: Stripe for payments, DocuSign for documents, SendGrid for email, Airtable and Google Sheets for data exchange, and Zapier, Make, and n8n for automation.
- AI where it adds value: OpenAI/ChatGPT powers AI-enabled functionality inside the product.
- Requirements into maintainable changes: business requirements are translated into product changes that stay maintainable in a large system.

## System & architecture

`Next.js` `TypeScript` `Supabase` `PostgreSQL` `OpenAI/ChatGPT` `Stripe` `DocuSign` `SendGrid` `Airtable` `Google Sheets` `Zapier` `Make` `n8n`

- Application: Next.js and TypeScript.
- Data: Supabase and PostgreSQL, with a relational model and permission rules.
- Integrations: payments, documents, email, spreadsheets, and automation tools, plus OpenAI/ChatGPT for AI features.
- Product areas: financial planning, CRM operations, reporting and dashboards, billing logic, documents, and admin workflows.

The exact production implementation and credentials remain private.

## Key challenge

Evolving a large live platform without disrupting the people using it. With 120k+ active users, years of accumulated workflows and data relationships, and integrations that touch payments, documents, and email, each change has to preserve established behavior, keep data consistent, and stay reliable in production.

![Complex data modeling: position detail](../assets/astutewheel/screenshots/position-detail.png)
![Client record detail](../assets/astutewheel/screenshots/personal-detail.png)

## Validation & production quality

- Production reliability: at 120k+ active users, performance, data integrity, maintainability, and operational clarity matter as much as feature delivery.
- Troubleshooting: production issues are traced to their cause across data, permissions, workflows, and integrations.
- Consistency: CRM, reporting, and financial data stay consistent as the product changes.
- Integrations: more than 10 production integrations are kept working alongside new functionality.

## Outcome

AstuteWheel is a mature live financial platform serving 120k+ active users across financial planning, CRM, reporting, payments, documents, integrations, and automation, and it keeps evolving without full rewrites. In the client's words:

> "What stands out most is his ability to take a high-level idea and translate it into a practical, well-designed solution that supports both our business needs and long-term scalability."

> "He has consistently demonstrated professionalism, problem-solving skills, and a strong commitment to delivering quality outcomes."

Andrew W., verified client

![Client review](../assets/testimonials/andrew-w-astutewheel.png)

## What this demonstrates

- Product decisions in a mature live system
- Evolving architecture without disrupting existing users
- Data integrity and permission design
- Integration and automation decisions across payments, documents, email, and spreadsheets
- AI-enabled functionality in production
- Production reliability and troubleshooting
- Translating business requirements into maintainable product changes

## Public portfolio note

This is a commercial production system. Source code, internal data, customer information, and proprietary implementation details are intentionally not public.
