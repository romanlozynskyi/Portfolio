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

The client already had a GPT-based sleep assistant, used mainly by parents asking about a child's sleep, but no product around it. I built the application from scratch and delivered it live as a customer-facing product with free and paid access. I owned the full scope: a mobile-first chat interface, signup and login, the OpenAI integration, Stripe subscriptions with account and billing screens, an embeddable chat widget for the client's own website, admin access for user management, and handover documentation.

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

- Free mode first: users open the app and start chatting immediately, sign up only when they want paid features, then go straight to plan selection and Stripe checkout.
- Assistant logic stays with the client: the app passes each message and the user's free or paid status to the client's GPT, which handles the sleep guidance, and holds no sleep logic of its own.
- Subscription state follows payment: Stripe webhooks drive the account status, so it updates the same way whether checkout started in the main app or elsewhere.
- Chat reliability: the chat handles an active assistant run and several messages sent in quick succession.
- One chat core, two surfaces: the full-page chat and the embeddable widget share the same chat core, while authentication and subscriptions stay in the main app.

![Free and paid plans. Presentation mockup, not a capture of the live app.](../assets/ai-sleep-assistant/screenshots/pricing.png)

## System & architecture

`OpenAI API` `Stripe` `Webhooks` `Embeddable widget`

The application layer is built on Bubble. Around it, the app coordinates these services and access states:

- AI layer: the OpenAI API produces the assistant's responses; each request carries the user's message and free or paid status.
- Billing: Stripe checkout and subscriptions, with webhooks keeping the account status in sync with payment.
- Access: signup and login, guest access in free mode, and free, paid, and gift access states.
- Distribution: a reusable chat core serving the full-page chat and the embeddable widget.
- Administration: admin access for user management.

## Validation & production quality

- End-to-end testing: the application was deployed live after testing the full flow.
- Fixes during testing: issues found were fixed quickly, as the client noted in the review.
- Payment correctness: webhook-driven status keeps the paid or free state consistent regardless of where checkout starts.
- Concurrency handling: the chat copes with an active assistant run and multiple quick messages.
- Handover: documentation and a Loom walkthrough were delivered so the client can manage updates going forward.

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
