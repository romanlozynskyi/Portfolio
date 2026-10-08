# Universal Lead Scout

**Category:** AI Agent / Research Automation / Lead Intelligence  
**Status:** Active development  
**Source code:** Private  
**Role:** Built the research agent: campaign orchestration, source adapters, verification, enrichment, scoring, and tests.  
**Problem:** Lead tools stop at discovery, so every company, person, and contact path still has to be checked by hand.  
**Result:** In a Bubble App Gallery campaign, 31 applications were enriched and 27 became contactable ICP leads, with 24 false identity matches rejected.  
**Metric:** 30 of 31 | applications confirmed active  
**Metric:** 23 | with a verified founder or owner  
**Metric:** 21 | with a contactable decision-maker  
**Metric:** 23 | with a verified LinkedIn path  
**Metric:** 27 | classified as contactable ICP leads  
**Metric:** 24 | false identity matches rejected  

## Overview

Universal Lead Scout is a campaign-oriented research agent that finds, verifies, and enriches leads.

It keeps working across sources and batches until a campaign reaches the requested number of qualified, contactable leads, or the available sources run out.

![Pipeline overview: sources, research, verification, enrichment, scoring, and qualified leads. The lead cards in the graphic are illustrative.](../assets/ai-lead-scout/cover/pipeline.png)

The user is whoever runs a lead campaign and needs qualified, contactable leads. Many lead tools stop after discovery: they return companies or contact records, and the user still has to answer the questions that matter:

- Is the company active and relevant to the campaign?
- Is this person the right decision-maker, and is the identity match reliable?
- Is there a usable contact path and enough evidence to justify outreach?

Universal Lead Scout moves those checks into the research pipeline.

I built the agent end to end. The areas I owned:

- Campaign orchestration and campaign state
- Source adapters and source routing, including cost policy
- Company and identity verification
- Contact enrichment, scoring, and deduplication
- Automated tests

## Product outcomes & evidence

Evidence from a Bubble App Gallery campaign that produced 31 unique applications for enrichment.

## Key product & engineering decisions

- Outcome-based campaigns: the agent runs until the target of qualified leads is met, not until one search stage finishes.
- Conservative verification: a name match alone is not enough, and weak or unsafe matches are rejected instead of passed through.
- Cheapest reliable source first: routing prefers official APIs and direct access before browser automation, search providers, and generic scraping.
- Cost as a routing rule: a campaign can enforce zero incremental spend or require approval before a metered provider is used.
- Capability and cost kept separate: a source marked as technically available cannot silently be treated as free.

Telling real matches from false ones. A candidate is not strong simply because a name appears to match, so the agent looks for supporting evidence such as company role, product ownership, profile history, or current activity.

False identity matches are rejected instead of being silently passed through as leads. In the Bubble App Gallery campaign, 24 false identity matches were rejected during verification.

## System & architecture

A campaign orchestrator drives source-specific adapters through one pipeline:

1. Interpret the campaign requirements and select suitable sources.
2. Discover candidate companies or products.
3. Verify that each company is active and relevant.
4. Identify the likely decision-maker and verify the identity with evidence.
5. Enrich contact paths such as LinkedIn, email, Instagram, Facebook, phone, or contact forms.
6. Score qualification and evidence quality, and reject weak or unsafe matches.
7. Deduplicate across sources.
8. Continue until the campaign target is reached or source capacity is exhausted.

`TypeScript` `Playwright` `Exa` `Apify` `Web Research` `Automation` `Data Enrichment`

Source routing prefers reliable, low-cost access and falls back only when needed:

1. Official API or data endpoint
2. Direct HTTP parsing
3. Local browser automation with Playwright
4. Search and enrichment providers such as Exa
5. Proven source-specific Apify Actors
6. Generic scraping providers, only when necessary

## Validation & production quality

- Automated tests cover source adapters, capability declarations, campaign behavior, cost policy, enrichment, and verification logic.
- A later architecture audit separated provider capability from incremental cost.
- A lead is counted only on evidence: verification rejects weak or unsafe matches before they reach the result.

## Outcome

In a Bubble App Gallery campaign, 31 unique applications were enriched: 30 were confirmed active, 23 had a verified founder or owner, and 27 were classified as contactable ICP leads. The result that matters is the reduction from candidates to evidence-backed, usable leads.

- Multi-source agent orchestration with outcome-based campaign logic
- Evidence-based verification of identity and contact data
- Source routing with fallbacks and cost-aware execution
- Deduplication and campaign state
- Test-driven agent development

## Public portfolio note

Production source code, provider credentials, private campaign data, and proprietary verification logic are intentionally omitted from this public case study.
