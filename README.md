# Freelance Opportunity Intelligence Pipeline

An automated opportunity-processing system that collects job listings, enriches details, matches roles to team capabilities, drafts tailored proposals, and sends operational alerts.

## Problem solved

Reviewing large volumes of freelance opportunities requires repeated browsing, qualification, skill matching, proposal preparation, duplicate checking, and follow-up tracking. This architecture turns those steps into a monitored data pipeline with explicit scoring and human review points.

## Architecture

```mermaid
flowchart LR
    S[Opportunity search] --> I[Search ingestion]
    I --> D[(Opportunity database)]
    D --> E[Detail enrichment]
    E --> M[Profile and skill matcher]
    M --> A[AI-assisted proposal drafting]
    A --> H[Human review queue]
    H --> G[Tracking sheet]
    I -.-> N[Operational alerts]
    E -.-> N
    A -.-> N
```

## Technology

Python · Selenium · Turso/libSQL · Google Sheets API · Slack webhooks · LLM APIs · Linux scheduling · Structured health monitoring

## Engineering highlights

- Separates discovery and detail enrichment into independent passes.
- De-duplicates opportunities and tracks retry state in a durable database.
- Scores opportunities against structured team profiles and evidence.
- Validates proposal structure and length before human review.
- Records health, backlog, overlap, and failure conditions.
- Keeps service-account keys, database tokens, webhooks, logs, and customer profiles private.

## Documentation

- [Architecture](docs/architecture.md)
- [Matching and proposal flow](docs/intelligence-flow.md)
- [Security and compliance](docs/security.md)

> This repository is an architecture showcase. Scraping implementation, anti-bot handling, service credentials, logs, personal profiles, and operational source are not published.
