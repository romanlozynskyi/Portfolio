# Universal Lead Scout

**Category:** AI Agent / Research Automation / Lead Intelligence  
**Status:** Active development  
**Source code:** Private  
**Role:** Built the research agent: campaign orchestration, source adapters, verification, enrichment, scoring, and tests.  
**Problem:** Lead tools stop at discovery, so every company, person, and contact path still has to be checked by hand.  
**Result:** In a Bubble App Gallery campaign, 31 applications were enriched and 27 became contactable ICP leads, with 24 false identity matches rejected.  
**Metric:** 30 of 31 | applications confirmed active | product | Of the 31 unique applications the campaign discovered, the company is real and still operating
**Metric:** 23 | with a verified founder or owner | product | Identity backed by evidence, not just a name match
**Metric:** 21 | with a contactable decision-maker | product | A decision-maker with a usable contact path
**Metric:** 23 | with a verified LinkedIn path | product | A verified route for outreach
**Metric:** 27 | classified as contactable ICP leads | product | Leads that fit the campaign's ideal customer profile and can actually be reached
**Metric:** 24 | false identity matches rejected | evidence | Plausible matches rejected instead of forced into the results, which favors quality over recall

## Overview

Universal Lead Scout is a campaign-oriented AI agent that sources, validates, qualifies, and completes contactable leads across multiple sources.

Most lead tools stop at discovery, leaving the checks to the user. This agent runs a campaign until it reaches the requested number of qualified, contactable leads or the sources run out: it routes across sources by cost, requires evidence before accepting a lead, and checks contactability. I built it end to end.

- Campaign orchestration and campaign state
- Source routing with a cost policy, and fallbacks across providers
- Company and identity verification against evidence, with scoring
- Contact enrichment, deduplication, and automated tests

![Pipeline overview: sources, research, verification, enrichment, scoring, and qualified leads. The lead cards in the graphic are illustrative.](../assets/ai-lead-scout/cover/pipeline.png)

## Product outcomes & evidence

Evidence from a Bubble App Gallery campaign that discovered and enriched 31 unique applications. The figures below count what survived verification, not raw discovery volume. In another flow, 47 candidates were reduced to 8 contactable leads.

## Key product & engineering decisions

- Quality and evidence before recall: weak or unsafe matches are rejected instead of being passed through, so the result is a smaller list that can be trusted.
- Evidence required before accepting a lead: a name match alone is never enough, so the agent looks for supporting evidence such as company role, product ownership, profile history, or current activity.
- Provider routing and fallback: routing prefers the cheapest reliable source, with official APIs and direct access before browser automation, search providers, and generic scraping, and it falls back only when needed.
- Contactability validation: contact paths such as LinkedIn, email, Instagram, Facebook, phone, or contact forms are enriched, and a lead counts as contactable only with a usable path to the right decision-maker.
- Cost controls, stop conditions, and deduplication: a campaign can enforce zero incremental spend or require approval before a metered provider is used, a source that is technically available is never silently treated as free, results are deduplicated across sources, and the campaign stops when the target is met or source capacity is exhausted.

## System & architecture

`TypeScript` `Playwright` `Exa` `Apify` `Web Research` `Automation` `Data Enrichment`

A campaign orchestrator drives source-specific adapters through one agent pipeline:

1. Campaign input: interpret the campaign requirements and select suitable sources.
2. Source discovery: find candidate companies or products.
3. Provider routing: use the cheapest reliable source first and fall back only when needed.
4. Evidence validation: verify that each company is active and relevant, then identify the likely decision-maker and verify the identity with evidence.
5. Scoring: score qualification and evidence quality, and reject weak or unsafe matches.
6. Contactability: enrich contact paths such as LinkedIn, email, Instagram, Facebook, phone, or contact forms.
7. Deduplication: remove duplicates across sources.
8. Final output: continue until the campaign target is reached or source capacity is exhausted.

The boundaries between steps are rule-based: the source routing order, the cost policy, the stop conditions, deduplication, and the evidence requirements for accepting a lead.

Provider details are secondary to that pipeline. Source routing tries these in order:

1. Official API or data endpoint
2. Direct HTTP parsing
3. Local browser automation with Playwright
4. Search and enrichment providers such as Exa
5. Proven source-specific Apify Actors
6. Generic scraping providers, only when necessary

## Validation & production quality

- Evidence-backed acceptance: a lead is counted only on evidence, and verification rejects weak or unsafe matches before they reach the result.
- Source verification: each company is verified as active and relevant before it is enriched.
- Contactability checks: a lead is classified as contactable only when a usable contact path exists.
- Deduplication: duplicates are removed across sources, so volume is not inflated.
- Provider fallback: routing falls back through the source order only when needed, and a later architecture audit separated provider capability from incremental cost.
- Cost limits: a campaign can enforce zero incremental spend or require approval before a metered provider is used.
- Boundary: the agent researches and qualifies leads, and it does not run outreach or automate logins.
- Automated tests: they cover source adapters, capability declarations, campaign behavior, cost policy, enrichment, and verification logic, and 469 tests passed after a provider and cost-model change.
- Completion over volume: results are counted as qualified, contactable leads, not as raw scraping volume.

## Outcome

Universal Lead Scout is a repeatable, evidence-driven research workflow: it turns a campaign brief into qualified, contactable leads, each backed by evidence, instead of handing back a list of raw candidates.

Capabilities demonstrated:

- Multi-source agent orchestration with outcome-based campaign logic
- Evidence-based validation of identity and contact data
- Cost-aware source routing with fallbacks and deduplication
- Test-driven agent development, built for repeatable runs

## Public portfolio note

Production source code, provider credentials, private campaign data, and proprietary verification logic are intentionally omitted from this public case study.
