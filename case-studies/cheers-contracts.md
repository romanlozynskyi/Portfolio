# Cheers

**Category:** Contract Management SaaS  
**Source code:** Private  
**Problem:** Contract work moves through many statuses, contacts, and team members, and needs one place to track it.  
**Result:** A workflow-heavy contract management product with a pipeline, analytics, a contact CRM, and team access control.  

## Overview

Cheers is a workflow-heavy contract management product that tracks contracts through a status pipeline, with analytics, a contact CRM, team access, notifications, and templates.

Its users are teams that manage contracts and the contacts behind them, where work moves through many statuses, contacts, and team members and needs one place to be tracked. I worked on the product and data structure design behind it: the contract and contact model, role-based access, and the integration hooks for billing, email, and SMS.

- Contract pipeline with status tracking
- Contact CRM and contact management
- Team management with role-based access
- Analytics, notifications, templates, search, and pagination

![Contract pipeline and analytics](../assets/cheers-contracts/cover/dashboard.jpg)

## Product outcomes & evidence

No numeric results are claimed. The evidence is the shipped product itself, as shown in its own screens.

- Contract pipeline: contracts are tracked through statuses such as draft, sent, active, and signed, with a summary of total, active, and soon-to-end contracts.
- Contract analytics: the portfolio is broken down by contract type, from client and services agreements to NDAs and statements of work.
- Financial visibility: a six-month forecast of revenue, payouts, and projected balances, plus sales by user and 30-day expected revenue and expenses.
- Contact CRM: a contacts portfolio organized by party type, covering clients, suppliers, partners, contractors, and representatives.
- Team access: team management with role-based access.
- Notifications and templates: in-product notifications and Cheers templates, with search and pagination across contracts.

![Mobile analytics overview](../assets/cheers-contracts/screenshots/mobile-overview.jpg)

## Key product & engineering decisions

- Contracts as a status pipeline: contracts are tracked through explicit statuses, and the dashboard summarizes them by status and by upcoming end date.
- Contacts as their own CRM: contacts are managed as records organized by party type, because contract work depends on the people behind each contract.
- Role-based access: a team works on the same contracts, with role-based access deciding what each member can do.
- Notifications and templates inside the workflow: they are part of the contract workflow itself rather than separate tools.
- Analytics for operational visibility: the dashboard turns contracts and contacts into charts of contracts by type, contacts by party type, and revenue and payout forecasts.

## System & architecture

The product is organized like this, based on its own navigation and screens:

- Application and workflows: a workflow-heavy web product with a contract pipeline, status tracking, notifications, templates, search, and pagination, usable on desktop and mobile.
- Data model: product and data structure design for contracts and contacts.
- Contracts and contacts: contracts organized by type and status, and contacts organized by party type.
- Roles and access: team management with role-based access.
- Integrations: hooks for billing, email, and SMS.
- Reporting and analytics: a dashboard with contract and contact breakdowns and forecasts of revenue, payouts, and expenses.

## Validation & production quality

- Responsive interface: the analytics view is delivered on both desktop and mobile.
- Data handling: only aggregate analytics views are shown publicly, and screens with counterparty names, contact details, or account records are excluded.

## Outcome

Cheers shows workflow-heavy SaaS product engineering: a contract pipeline, contact CRM, team access, analytics, and integration hooks designed as one product.

Capabilities demonstrated:

- Workflow-heavy SaaS design, from pipelines and statuses to role-based access
- Data structure design for contracts and contacts
- Integration hooks for billing, email, and SMS
- Operational UX across analytics, notifications, and templates

## Public portfolio note

Screens that show specific counterparty names, contact details, or account records are intentionally excluded from this public case study; only aggregate analytics views are shown.
