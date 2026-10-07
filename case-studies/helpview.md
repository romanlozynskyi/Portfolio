# Helpview

**Category:** SaaS / Knowledge Base / Notion Integration  
**Live:** https://helpview.so/  
**Source code:** Private  
**Role:** Product engineering on a Bubble-based SaaS: content sync, publishing, search, theming, custom domains, analytics, and the embedded widget.  
**Problem:** Teams want to keep writing in Notion, but customers need a searchable, branded help center.  
**Result:** A live product that publishes one Notion content source as a help center, documentation, and an embedded widget, with search analytics that expose content gaps.  

## Overview

Helpview turns Notion content into a structured, searchable customer help center. Teams continue writing in Notion while Helpview handles the customer-facing publishing experience.

The product connects one content source to multiple support surfaces such as a help center, documentation, and an embedded help widget.

![Published help center](../assets/helpview/cover/help-center.png)

## Problem & users

The users are teams that write their documentation in Notion and need to give customers a real help center, along with the customers who search it. The product has to cover publishing, search, branding, and measuring what customers cannot find.

## My role & ownership

I worked on the product as an engineer on the full SaaS, not only the page layer. The areas I owned:

- Content synchronization from Notion
- Data structure and publishing state
- Search, theming, and multi-language publishing
- Custom domains and permissions
- Analytics and the embedded support widget

## Product outcomes & evidence

What the product delivers, visible in the live product at helpview.so:

- Notion pages published as customer-facing help content
- A searchable help center, a help widget, and SEO-friendly publishing
- Theme and brand customization, multiple languages, and custom domains
- Search insights, including zero-result searches and content gaps

![Dashboard and search analytics](../assets/helpview/screenshots/dashboard.png)

## Product decisions

- Notion stays the editing source: teams keep writing where they already write, and Helpview handles the customer-facing side.
- One content model, many surfaces: the same content feeds the help center, documentation, and the embedded widget.
- Analytics close the loop: search behavior, zero-result searches, and content gaps feed back into improving the documentation.

![Theme and brand customization](../assets/helpview/screenshots/customization.png)

## System & architecture

`Bubble` `Notion`

The product coordinates content synchronization, data structure, publishing state, search, theming, permissions, custom domains, analytics, and an embedded support experience. The application layer is built on Bubble, while the engineering focus is SaaS architecture, workflows, integrations, and user-facing support experiences rather than only page construction.

1. Connect the Notion workspace.
2. Select and organize help content.
3. Configure the help center style and behavior.
4. Publish to a Helpview subdomain or custom domain.
5. Keep Notion as the editing source.
6. Use search behavior and analytics to improve documentation over time.

![Notion sync settings](../assets/helpview/screenshots/settings-sync.png)

## Key challenge

Coordinating one content source across several surfaces. The product requires coordination across content synchronization, data structure, publishing state, search, theming, permissions, custom domains, analytics, and an embedded support experience.

![Publish Notion pages as customer-facing help content](../assets/helpview/screenshots/articles.png)

## Outcome

Helpview is live at helpview.so: teams connect a Notion workspace, publish a searchable help center on a subdomain or custom domain, and use search analytics to find gaps in their documentation.

## What this demonstrates

- SaaS product development around a third-party content source
- Notion integration workflows and content synchronization
- Search and knowledge base UX across multi-surface publishing
- Customization, theming, and embedded widget flows
- Analytics-driven product feedback

## Public portfolio note

The production code and internal implementation remain private. Public information in this case study is limited to product behavior and architecture-level work.
