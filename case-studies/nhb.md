# Nothing Held Back (NHB)

**Category:** SaaS / Membership & Coaching Platform  
**Live:** https://app.nothingheldback.com/login  
**Live label:** Open live app  
**Website:** https://www.nothingheldback.com/  
**Source code:** Private  
**Role:** Systems-level engineer: around a year on the membership and community platform, covering performance, abuse prevention, billing reconciliation, three product areas, and admin analytics.  
**Problem:** A growing membership and coaching platform needed to hold up under scale, with account sharing, geographic restrictions, and billing accuracy under control.  
**Result:** A unified, multi-surface growth and community platform: 23 apps in one platform for 48,495+ community members, with 3-5 weekly live content sessions.  
**Metric:** 48,495+ | community members | product  
**Metric:** 23 | apps in one platform | product  
**Metric:** 3-5 | weekly live content sessions | product  

## Overview

Nothing Held Back (NHB) is a membership and coaching platform for entrepreneurs: 23 apps in one platform for 48,495+ community members, with live coaching calls and tiered paid membership.

Its users are entrepreneurs who join as members, from free community access up to paid plans, and the coaches who run programs for them. I worked on NHB for around a year as the systems-level engineer, brought in for the hard backend and product work a scaling platform needs rather than surface-level features.

- Ownership of the Library, Resources, and Fast Feedback areas, including a full Fast Feedback redesign
- An admin analytics dashboard built from scratch
- A performance audit, account-sharing prevention, and geo-blocking
- Billing reconciliation and root-cause debugging

![NHB Home dashboard](../assets/nhb/cover/home-dashboard.png)
![Coaching library and featured coaches](../assets/nhb/screenshots/library.png)
![Resource hub: templates, swipe files, and tools](../assets/nhb/screenshots/resources.png)

## Product outcomes & evidence

The platform's reach and breadth lead the evidence: a large community, many apps in one platform, and live content every week. The client's review is supporting social proof.

In the client's words:

> "He shipped a lot in that time, but what I valued most was that we could hand him the hard, systems-level stuff and not worry about it."

![Client review (original screenshot). This testimonial refers to an earlier version of the product. The case study above describes the current implementation and architecture.](../assets/testimonials/max-iver-nhb.png)

## Key product & engineering decisions

- Performance and capacity audit: the engagement began with an audit of the live app, tracing database searches, workflows, and data fetching to find where the load was really coming from before the scaling push.
- Account-sharing prevention: a Netflix-style system, where device fingerprinting, IP/geo signals, and session limits were researched and their tradeoffs weighed before an approach was chosen.
- Geo-blocking inside the app: infrastructure-level blocking was not possible, so it was built into the application, with IP country detection and a configuration that can change without a redeploy.
- Billing reconciliation with safety checks: a tool parsed thousands of subscription records, cross-checked them against the database, and flagged only genuine mismatches for review, so nothing was cancelled by accident.
- Ownership and root cause: Library, Resources, and Fast Feedback (including its full redesign) plus an admin analytics dashboard built from the ground up, with problems traced to their actual cause instead of patched at the symptom.

## System & architecture

`Next.js` `TypeScript` `Supabase` `PostgreSQL` `APIs` `Automation` `AI integrations` `Google OAuth`

Based on the product's own navigation and screens, the platform is organized like this:

- Application: Next.js and TypeScript, behind a home feed, a content library by coach and program, a resource hub, community forums, and live coaching calls ("Hot Seats") with a calendar and recordings.
- Data: Supabase and PostgreSQL.
- Auth and access: email/password and Google OAuth login, invite-code signup, and tiered membership (Free, Plus, Pro, Fast Forward) that gates resources.
- Billing: subscription records reconciled against the database, with safety checks against accidental cancellations.
- Automation and AI: APIs, automation, and AI integrations connect the platform's surfaces.
- Production: capacity and performance investigated on the live app, with geo-blocking rules that change without a redeploy.

![Community forums](../assets/nhb/screenshots/forums.png)
![Login and membership entry](../assets/nhb/screenshots/login.png)

## Validation & production quality

- Capacity investigation: the performance audit ran on the live app to find the heaviest capacity drains before scaling.
- Billing safety checks: reconciliation cross-checks subscription records against the database, flags only genuine mismatches, and guards against accidental cancellations.
- Production debugging: problems were traced to their actual cause rather than patched at the symptom.
- Access controls: account sharing was addressed with a system chosen after weighing device, IP/geo, and session signals, and geo-blocking rules can be changed without a redeploy.

## Outcome

The hard, systems-level work behind a growing membership platform was handed over and handled reliably, so the team did not have to worry about it.

Capabilities demonstrated:

- Systems-level engineering on a live, scaling platform
- Performance and capacity auditing
- Abuse-prevention design: account sharing and geographic restrictions
- Data reconciliation tooling with safety checks against destructive automation
- Ownership of product surfaces, with admin tooling built from scratch

## Public portfolio note

Figures visible in the screenshots (for example member counts and content counts) reflect a single point in time and are not claimed as current. Source code, customer data, and internal implementation details are not public.
