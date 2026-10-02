# AI Lead Scout

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

AI Lead Scout is a campaign-oriented research agent that finds, verifies, and enriches leads.

It keeps working across sources and batches until a campaign reaches the requested number of qualified, contactable leads, or the available sources run out.

![Pipeline overview: sources, research, verification, enrichment, scoring, and qualified leads. The lead cards in the graphic are illustrative.](../assets/ai-lead-scout/cover/pipeline.png)

## Problem

Many lead tools stop after discovery. They return companies or contact records, and the user still has to answer the questions that matter:

- Is the company active and relevant to the campaign?
- Is this person the right decision-maker, and is the identity match reliable?
- Is there a usable contact path and enough evidence to justify outreach?

AI Lead Scout moves those checks into the research pipeline.

## What I built

A campaign orchestrator drives source-specific adapters through one pipeline:

1. Interpret the campaign requirements and select suitable sources.
2. Discover candidate companies or products.
3. Verify that each company is active and relevant.
4. Identify the likely decision-maker and verify the identity with evidence.
5. Enrich contact paths such as LinkedIn, email, Instagram, Facebook, phone, or contact forms.
6. Score qualification and evidence quality, and reject weak or unsafe matches.
7. Deduplicate across sources.
8. Continue until the campaign target is reached or source capacity is exhausted.

## Stack and architecture

`TypeScript` `Playwright` `Exa` `Apify` `Web Research` `Automation` `Data Enrichment`

Source routing prefers reliable, low-cost access and falls back only when needed:

1. Official API or data endpoint
2. Direct HTTP parsing
3. Local browser automation with Playwright
4. Search and enrichment providers such as Exa
5. Proven source-specific Apify Actors
6. Generic scraping providers, only when necessary

Cost is part of the routing logic. A campaign can enforce zero incremental spend or require approval before a metered provider is used.

## Key decisions

- Campaigns are outcome-based: the agent runs until the target of qualified leads is met, not until one search stage finishes.
- Verification is conservative: a name match alone is not enough. The agent looks for supporting evidence such as company role, product ownership, profile history, or current activity, and rejects false identity matches instead of passing them through.
- Capability and cost are separate: a later architecture audit made sure a source marked as technically available cannot silently be treated as free.
- Automated tests cover source adapters, capability declarations, campaign behavior, cost policy, enrichment, and verification logic.

## Results and evidence

A Bubble App Gallery campaign produced 31 unique applications for enrichment. The important result is not the discovery count but the reduction from candidates to evidence-backed, usable leads: 27 were classified as contactable ICP leads, and 24 false identity matches were rejected during verification.

## Public portfolio note

Production source code, provider credentials, private campaign data, and proprietary verification logic are intentionally omitted from this public case study.
