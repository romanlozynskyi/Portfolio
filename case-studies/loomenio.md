# Loomenio

**Category:** AI-first SaaS / Inventory / Production Operations  
**Live:** https://app.loomenio.com  
**Source code:** Private  
**Role:** Product engineer: designed and built the architecture, data model, permissions, inventory and production logic, AI workflows, integrations, and the responsive experience.  
**Problem:** Small-batch makers keep inventory, recipes, suppliers, and production in disconnected tools, so what needs attention next is never obvious.  
**Result:** 50% faster operational data capture, 30% fewer manual corrections, and under a minute to identify the next operational priority.  
**Metric:** 50% | faster operational data capture | product  
**Metric:** 30% | fewer manual corrections | product  
**Metric:** Under 1 min | to identify the next operational priority | product  
**Metric:** 98.6% | operation-type accuracy | evidence | 85-case live evaluation  
**Metric:** 100% | entity accuracy for auto-filled entities | evidence | 85-case live evaluation  
**Metric:** 1,491 | automated tests | evidence  
**Metric:** 85 | cases in the live evaluation | evidence  

## Overview

Loomenio is an operations platform for small-batch manufacturers. It brings inventory, recipes, production, sales, suppliers, imports, integrations, and operational decision support into one product.

Its users are small-batch makers whose inventory, recipes, supplier prices, and production live in separate spreadsheets, so the next action is never obvious. The app is built to show what needs attention next, without handing critical business logic to an LLM. I designed and built it end to end, from the data model and permissions to the AI workflows and the responsive interface.

- Product architecture and the multi-workspace data model
- Inventory, production, and recipe logic
- AI-assisted workflows, including AI Capture and the explanations in Today
- Integrations, analytics foundations, and the responsive application experience

![Today, the operational recommendation view](../assets/loomenio/cover/today.png)

## Product outcomes & evidence

Outcomes for the product, and the AI and engineering evidence behind them.

## Key product & engineering decisions

- Deterministic business logic: inventory, costing, permissions, and production decisions stay deterministic and auditable. Today's recommendations come from calculations for demand rate, stock cover, reorder points, and margin, and the LLM only translates or explains them.
- AI only where it helps: AI interprets messy user input and explains system output. It does not decide what is written to inventory.
- Structured output and validation: AI Capture turns messy input into a structured proposal. Ambiguous input and unclear or mismatched units go to review instead of being guessed.
- Confirmation before changes: the user confirms a structured proposal before anything is applied. Sales support reversals and inventory changes are kept as a transaction history, so records are never silently overwritten.
- Multi-workspace security: accounts can belong to several workspaces, and membership with role-based permissions decides what each person can do, enforced by row-level security.

![AI-assisted data capture](../assets/loomenio/screenshots/ai-capture.png)
![Sales and reversals](../assets/loomenio/screenshots/sales.png)

## System & architecture

`Next.js` `TypeScript` `Supabase` `PostgreSQL` `RLS` `OpenAI API` `Vercel`

Loomenio is a multi-workspace SaaS application, organized into these layers:

- Application: a Next.js and TypeScript application with services for inventory transactions, production and recipes, orders and suppliers, notifications, Today recommendations, and AI Capture.
- Data and security: Supabase and PostgreSQL, with row-level security isolating each workspace and owner, admin, member, and viewer roles controlling access.
- AI layer: the OpenAI API interprets input in AI Capture and explains Today's recommendations. The pipeline parses input, detects the operation type, resolves entities and units, preserves totals and cost semantics, routes ambiguity to review, and builds a structured proposal that needs confirmation.
- Integrations: provider-independent integration ingestion, CSV import, and notifications through queues, rules, and deliveries.
- Deployment: hosted on Vercel.

![Products and recipes](../assets/loomenio/screenshots/products.png)

## Validation & production quality

- Automated tests: 1,491 automated tests cover the product.
- Live evaluation: an 85-case evaluation set reached 98.6% operation-type accuracy, with 100% entity accuracy for auto-filled entities.
- Ambiguity routing: unclear input and mismatched units go to review instead of silently applying bad quantities.
- Data isolation: row-level security keeps each workspace's data separate, and critical operations are validated in both the application and the database.
- Imports: the import system enforces uniqueness and validation on structured data.
- Production hardening: production debugging, plus responsive and acceptance QA.

![CSV import](../assets/loomenio/screenshots/import.png)

## Outcome

Loomenio is live as a production SaaS product that helps small-batch makers see what needs attention next, with AI where it helps and deterministic logic where it counts.

Capabilities demonstrated:

- End-to-end product ownership, from problem framing to production
- AI with deterministic safeguards, where AI interprets and deterministic logic decides
- Multi-workspace SaaS architecture with role-based access and row-level security
- Evaluation-driven quality, backed by a live evaluation set and automated tests
- Product decisions under real operational constraints, such as messy input and exact inventory and costing

## Public portfolio note

The production repository is private. This case study intentionally shows product architecture, workflows, screenshots, and engineering decisions without exposing proprietary source code or customer data.
