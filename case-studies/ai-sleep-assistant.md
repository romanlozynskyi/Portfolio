# AI Sleep Assistant

**Category:** AI Product / Client SaaS / Subscription App  
**Live:** https://kim-sleep-assistant-62596.bubbleapps.io/  
**Source code:** Private  
**Work period:** Nov 2025 to Jan 2026  
**Role:** Built the app from scratch and delivered it live: chat interface, OpenAI and Stripe integration, embeddable chat widget, admin access, and documentation.  
**Problem:** A sleep consulting business needed its existing GPT-based assistant turned into a customer-facing product with free and paid access.  
**Result:** Delivered live after end-to-end testing. The client confirmed the app and the Stripe flow worked well and left a 5-star review.  
**Metric:** 5.0 | Client rating  

## Overview

AI Sleep Assistant is a responsive AI chat product built for a sleep consulting business.

I owned this product end to end: built from scratch and delivered live, from scope and architecture to integrations, testing, launch, and handover.

The client already had a GPT-based sleep assistant, used mainly by parents asking about a child's sleep, but no product around it. The scope covered a mobile-first chat interface, signup and login, the OpenAI integration, Stripe subscriptions with account and billing screens, an embeddable chat widget for the client's own website, admin access for user management, and handover documentation.

![Chat interface. Presentation mockup, not a capture of the live app.](../assets/ai-sleep-assistant/cover/chat.png)

## Product outcomes & evidence

What shipped, and what the client said about it.

- Live in production: deployed after end-to-end testing, with free and paid access in one app.
- AI assistant integration: every message reaches the client's GPT together with the user's free or paid status.
- Subscriptions: Stripe checkout and plan selection, with the account status updated after payment.
- Embeddable widget: the same assistant also runs as a chat widget on the client's own website.

![Responsive chat on mobile, with login and widget views. Presentation mockup, not a capture of the live app.](../assets/ai-sleep-assistant/screenshots/mobile.png)
![Account and subscription management. Presentation mockup, not a capture of the live app.](../assets/ai-sleep-assistant/screenshots/account.png)

The client left a 5-star review (5.0).

> "He communicated clearly throughout, and fixed issues quickly during testing."

![Client review from Kim Rogers, Founder. Original screenshot, with the project title row cropped.](../assets/testimonials/upwork-review-01-clean.png)

## Key product & engineering decisions

- Free mode first: chat starts with no signup. Accounts and checkout come only when paid features are needed.
- Assistant logic stays with the client: the app sends each message and the free or paid status to the client's GPT. No sleep logic lives in the app.
- Subscription state follows payment: Stripe webhooks set the account status, so it stays correct wherever checkout starts.
- Chat reliability: an active assistant run and several quick messages are handled without breaking the chat.
- One chat core, two surfaces: the full-page chat and the widget share one core, while auth and billing stay in the main app.

![Free and paid plans. Presentation mockup, not a capture of the live app.](../assets/ai-sleep-assistant/screenshots/pricing.png)

## System & architecture

`Next.js` `TypeScript` `Supabase` `PostgreSQL` `OpenAI API` `Stripe`

The current implementation is built on the stack above and coordinates these layers and access states:

- Application: Next.js and TypeScript.
- Data: Supabase and PostgreSQL.
- AI layer: the OpenAI API answers; each request carries the message and the free or paid status.
- Billing: Stripe checkout and subscriptions, with webhooks syncing the account status to payment.
- Access: signup and login, guest mode, and free, paid, and gift states.
- Distribution: one reusable chat core for the full-page chat and the widget.
- Administration: admin access for user management.

## Validation & production quality

- End-to-end testing: the full flow was tested before the live launch.
- Fixes during testing: issues were fixed quickly, as the client noted in the review.
- Payment correctness: webhook-driven status keeps the paid and free states consistent.
- Concurrency handling: active assistant runs and quick successive messages are handled.
- Handover: documentation and a Loom walkthrough let the client manage updates.

## Outcome

AI Sleep Assistant went live as a client application with free and paid access, OpenAI-powered chat, Stripe subscriptions, and an embeddable chat widget. The client confirmed the app and the Stripe flow were working well and left a 5-star review.

Capabilities demonstrated:

- AI product integration with a client-owned assistant
- Subscription and payment logic with consistent state
- End-to-end product ownership, from scope to live launch
- Debugging and production delivery, including client handover
- Mobile-first chat UX and guest-to-paid conversion flows

## Public portfolio note

Private API credentials, assistant instructions, customer data, and production implementation details are intentionally excluded. The interface visuals on this page are presentation mockups, not captures of the live app.
