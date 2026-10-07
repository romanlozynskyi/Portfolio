# Voltt

**Category:** Product Rebuild / Startup Platform  
**Status:** In progress  
**Source code:** Private  
**Problem:** The current version reflects short-term prototype decisions, so the rebuild starts from architecture to support product growth.  
**Result:** Rebuild in progress, with an early startup diagnostic dashboard already in place.  

## Overview

Voltt is entering a rebuild phase. The work is being approached architecture-first so the new implementation can support product growth instead of reproducing short-term prototype decisions.

![Startup diagnostic dashboard](../assets/voltt/cover/dashboard.jpg)

## Problem & users

The users are startup teams assessing their readiness. The product is a startup diagnostic platform, and its current version carries short-term prototype decisions that the rebuild is meant to leave behind.

## Product decisions

- Architecture first: the new implementation is designed to support product growth instead of reproducing prototype shortcuts.
- Reasoning on record: an architecture log is kept from the beginning, so the final case study preserves the reasoning behind major product decisions instead of reconstructing them later.

## System & architecture

An early build of the startup diagnostic dashboard is already in place, covering an overall readiness score, per-dimension diagnostics, a 7/30/90-day roadmap, an evidence tracker, and an AI coach panel.

## Outcome

The rebuild is in progress. This case study will be expanded as implementation starts, documenting decisions and outcomes without exposing the private production repository. Planned areas to document:

- Product architecture and database model
- Workflow boundaries, authentication, and permissions
- AI and API integration strategy
- Deployment architecture and scalability decisions
- Migration from the current version, with milestone screenshots and release notes
