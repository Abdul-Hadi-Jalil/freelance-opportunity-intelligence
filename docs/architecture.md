# Architecture

```mermaid
flowchart TB
    subgraph Collection
      SEARCH[Search collector]
      DETAIL[Detail enricher]
    end
    subgraph Intelligence
      SKILL[Skill taxonomy]
      MATCH[Profile matcher]
      DRAFT[Proposal generator]
      CHECK[Rule validator]
    end
    subgraph Operations
      DB[(Durable job state)]
      SHEET[Review and tracking sheet]
      ALERT[Health and backlog alerts]
    end
    SEARCH --> DB --> DETAIL --> DB
    DB --> MATCH
    SKILL --> MATCH --> DRAFT --> CHECK --> SHEET
    SEARCH -.-> ALERT
    DETAIL -.-> ALERT
    CHECK -.-> ALERT
```

The collection layer owns retrieval and normalization. The intelligence layer categorizes skills, selects relevant profiles, drafts proposals, and applies deterministic quality checks. The operations layer preserves state and exposes work for review.
