# Helpview

**Category:** SaaS / Knowledge Base / Notion Integration  
**Live:** https://helpview.so/  
**Source code:** Private  
**Role:** Product engineering on a Notion-powered help center SaaS: content sync, publishing, search, theming, custom domains, analytics, and the embedded widget.  
**Problem:** Teams want to keep writing in Notion, but customers need a searchable, branded help center.  
**Result:** A live product that publishes one Notion content source as a help center, documentation, and an embedded widget, with synced publishing and search analytics that expose content gaps.  
**Metric:** 3 | customer-facing surfaces from one Notion content source | product | Help center, documentation, and an embedded help widget  
**Metric:** 3-step | publishing flow | product | Connect Notion, organize content, publish  
**Metric:** Search | with zero-result analytics | product | Shows what customers cannot find  
**Metric:** Synced | publishing from Notion | product | Notion stays the editing source  

## Overview

Helpview turns Notion content into a structured, searchable customer help center. Teams continue writing in Notion while Helpview handles the customer-facing publishing experience.

Its users are teams that write documentation in Notion and the customers who search it. I worked on Helpview as an engineer on the full SaaS, not only the page layer, owning the product architecture, Notion sync, publishing flow, search and discovery, analytics, and the customer-facing surfaces.

- Notion synchronization and the data structure behind publishing state
- Publishing flow, custom domains, and permissions
- Search, zero-result analytics, and multi-language publishing
- Theming and the embedded support widget

![Published help center](../assets/helpview/cover/help-center.png)

## Product outcomes & evidence

What the product delivers, visible in the live product at helpview.so.

![Dashboard and search analytics](../assets/helpview/screenshots/dashboard.png)

## Key product & engineering decisions

- One source of truth from Notion: teams keep writing where they already write, and Notion stays the editing source while Helpview handles the customer-facing side.
- Sync and publishing architecture: Helpview manages presentation and configuration on top of the Notion content. Nested Notion API responses and expiring Notion image URLs are handled in the sync, and heavy parsing and integration work is kept out of the application layer where that helps.
- Search with a zero-result feedback loop: search behavior and zero-result searches show what customers cannot find, and those content gaps feed back into the documentation.
- Content management apart from customer-facing delivery: one content model feeds the help center, documentation, and embedded widget, while theming, branding, and custom domains are configured separately, and content localization is kept apart from UI localization.

![Publish Notion pages as customer-facing help content](../assets/helpview/screenshots/articles.png)
![Theme and brand customization](../assets/helpview/screenshots/customization.png)

## System & architecture

`Next.js` `TypeScript` `Supabase` `Notion API` `Cloudflare Workers` `Vercel`

The product coordinates content synchronization, data structure, publishing state, search, theming, permissions, custom domains, analytics, and an embedded support experience, organized like this:

- Application: Next.js and TypeScript.
- Data: Supabase and PostgreSQL, holding the data structure and publishing state.
- Sync and publishing: the Notion API feeds content sync, and Cloudflare Workers are part of the production stack, with heavy parsing and integration work kept out of the application layer where useful.
- Storage: Cloudflare R2 holds permanent copies of assets, because Notion image URLs expire.
- Search and analytics: search across the published help content, with zero-result tracking that shows what customers cannot find.
- Deployment: Vercel, publishing to a Helpview subdomain or a custom domain.

Publishing takes three steps:

1. Connect the Notion workspace.
2. Select and organize help content, and configure the help center style and behavior.
3. Publish to a Helpview subdomain or custom domain.

![Notion sync settings](../assets/helpview/screenshots/settings-sync.png)

## Validation & production quality

- Sync consistency: sync behavior was debugged against nested Notion API responses, so the published content follows the Notion source.
- Asset durability: expiring Notion image URLs are replaced by permanent stored copies, so published images keep working.
- Search behavior: indexing and search tradeoffs were worked through, and zero-result searches are tracked to expose content gaps.
- Publishing: the three-step flow publishes to a Helpview subdomain or custom domain, and runs in the live product.
- Interface consistency: responsive behavior, mobile navigation, and theme consistency were worked through across the customer-facing surfaces.

## Outcome

Helpview is live at helpview.so, giving teams that write in Notion a real, branded help center without leaving their editor.

Capabilities demonstrated:

- One content source published as a help center, documentation, and an embedded widget
- Discoverability through a searchable help center
- Feedback loops: zero-result searches and content gaps flow back into the documentation
- Production publishing synced from Notion, to a subdomain or custom domain
- Customer-facing product UX, from theming and branding to multiple languages

## Public portfolio note

The production code and internal implementation remain private. Public information in this case study is limited to product behavior and architecture-level work.
