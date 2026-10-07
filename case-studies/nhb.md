# Nothing Held Back (NHB)

**Category:** SaaS / Membership & Coaching Platform  
**Stack:** Bubble.io  
**Source code:** Private  
**Role:** Systems-level engineering on a Bubble.io membership platform for around a year, per the client: performance, abuse prevention, billing reconciliation, three product areas, and admin analytics.  
**Problem:** A growing membership and coaching platform needed to hold up under scale, with account sharing, geographic restrictions, and billing accuracy under control.  
**Result:** In the client's words, the hard, systems-level work could be handed over with confidence, and the product shipped a lot over the engagement.  

## Overview

Nothing Held Back (NHB) is a membership and coaching platform for entrepreneurs, built on Bubble.io. The product combines a content library, a resource hub, community forums, live coaching calls, and tiered paid membership into one workspace.

According to the client, Roman worked on NHB for around a year, brought in for the systems-level engineering behind the product rather than surface-level feature work.

![NHB Home dashboard](../assets/nhb/cover/home-dashboard.png)

## Problem & users

The users are entrepreneurs who join as members, from free community access up to paid plans, and the coaches who run programs for them. As the client describes the engagement, the platform faced a scaling push and the problems that come with it: heavy capacity drains, shared accounts, geographic restrictions, and subscription records that had to match the database.

## My role & ownership

According to the client, the engagement covered:

- Ownership of the Library, Resources, and Fast Feedback areas of the product, including a full Fast Feedback redesign
- An admin analytics dashboard built from scratch
- A performance audit, an account-sharing prevention system, geo-blocking, and a billing reconciliation tool
- Root-cause debugging rather than symptom-patching

![Coaching library and featured coaches](../assets/nhb/screenshots/library.png)
![Resource hub: templates, swipe files, and tools](../assets/nhb/screenshots/resources.png)

## Product outcomes & evidence

The evidence for this case is the client's own account of the engagement:

> "He shipped a lot in that time, but what I valued most was that we could hand him the hard, systems-level stuff and not worry about it."

> "Roman is reliable, he thinks things through, and he's genuinely strong on the architecture side."

Max Iver, Head of Design at Nothing Held Back

![Client review](../assets/testimonials/max-iver-nhb.png)

## Product decisions

- Account sharing: a Netflix-style prevention system, with device fingerprinting, IP/geo signals, and session limits evaluated before choosing an approach.
- Geo-blocking in the application: infrastructure-level blocking was not an option, so it was built into the application itself, including IP country detection and a configuration that can change without a redeploy.
- Billing reconciliation: a tool that parsed subscription records, cross-checked them against the database, and flagged only genuine mismatches for review, with safety checks against accidental cancellations.
- Root cause over symptoms: problems were debugged to their cause rather than patched.

## System & architecture

The product runs on Bubble.io. Based on the product's own navigation and screens, its surface includes:

- A home feed with platform updates, community stats, and personalized activity
- A content library organized by coach and program
- A resource hub of templates, swipe files, and tools, gated by membership tier (Free, Plus, Pro, Fast Forward)
- Community forums organized into topic- and program-specific categories
- Live coaching calls ("Hot Seats") with a calendar and call recordings
- Email/password and Google OAuth login, invite-code signup, and tiered membership

![Community forums](../assets/nhb/screenshots/forums.png)
![Login and membership entry](../assets/nhb/screenshots/login.png)

## Key challenge

Preparing a live platform for a scaling push. The engagement began with a performance audit of the live app to identify the heaviest capacity drains before scaling.

## Validation & production quality

- The billing reconciliation tool cross-checks subscription records against the database and includes safety checks against accidental cancellations.
- The performance audit was run on the live app to identify the heaviest capacity drains.
- Geo-blocking configuration can be changed without a redeploy.

## Outcome

Per the client, the engagement delivered a performance audit, account-sharing prevention, geo-blocking, billing reconciliation, redesigned and owned product areas, and a new admin analytics dashboard, with hard systems-level work handled reliably.

## What this demonstrates

- Performance auditing and capacity planning under real scaling pressure
- Abuse-prevention system design: account-sharing prevention and geo-blocking
- Data reconciliation tooling with safety checks against destructive automation
- Ownership of entire product surfaces rather than isolated tickets
- Admin tooling built from scratch and root-cause debugging discipline

## Public portfolio note

This case study is built only from product screenshots and a client testimonial provided directly, with no other source material (contracts, dates, internal documentation) available at the time of writing. Figures visible in the screenshots (for example member counts and content counts) reflect a single point in time and are not claimed as current.
