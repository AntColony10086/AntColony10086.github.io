---
title: "ScopeGraph · Multi-Agent GraphRAG Carbon Assistant"
excerpt: "A LangGraph supervisor over 5 sub-agents on a Neo4j carbon knowledge graph. Hybrid Text2Cypher + vector retrieval, 3-layer per-tenant data isolation (JWT → state → Cypher whitelist), LLM-as-Judge grounding check, SSE streaming.<br/><img src='/images/proj-co2copilot.png?v=9' style='max-width:520px'>"
collection: portfolio
date: 2024-09-01
permalink: /portfolio/scopegraph/
redirect_from:
  - /portfolio/co2-copilot/
---

**Role**: Author / maintainer · core member · 2024.09 – present

**Repo**: <https://github.com/AntColony10086/ScopeGraph> · MIT · LangGraph + Neo4j + Vue 3

**One-liner**: A conversational carbon-emissions data assistant. The name "ScopeGraph" reflects three layers it scopes simultaneously: GHG-Protocol **Scope 1 / 2 / 3**, **scope of access** (strict per-tenant boundaries), and **scope of retrieval** (hybrid Text2Cypher + vector over a single graph). Ask in natural language; get structured answers with units, sources, comparisons, and interpretation.

**Architecture**

```
        user query (NL, zh / en)
               │
               ▼
        [Supervisor]            ← LangGraph
               │
        ┌──────┴────────────┬──────────────┐
        ▼                   ▼              ▼
  [router]         [additional_info]  [graphrag_query]
intent class.     ambiguity resolution  Text2Cypher + vector
        │                   │              │
        └─────────┬─────────┴──────────────┘
                  ▼
        [hallucination_check]   ← independent grounding judge (small LLM)
                  ▼
         streamed answer (SSE)
```

Five sub-agents under one supervisor; everything streams over SSE with a 5-layer fallback chain (3 stream attempts + 2 non-stream retries) so reasoning models with `<think>...</think>` blocks work cleanly.

**My contribution**

- LangGraph supervisor + 5 sub-agents (router, additional_info, graphrag_query, hallucination check, file/image handling).
- Hybrid retrieval over Neo4j: **Text2Cypher** for structured graph queries fused with multilingual vector search (`paraphrase-multilingual-MiniLM-L12-v2`).
- **3-layer per-tenant data isolation**: JWT claims → graph state → injected Cypher whitelist. Admin sees all enterprises; per-tenant accounts can only query their bound enterprise. (Real RBAC, not a prompt instruction.)
- **Anti-hallucination**: small-model independent grounding judge; low-confidence answers are annotated with a warning rather than silently emitted.
- Reasoning-model-friendly LLM layer: strips `<think>...</think>` blocks, falls through 3 structured-output methods (`json_schema` → `function_calling` → manual JSON parse). Provider-swappable to MiniMax / OpenAI / local LM Studio with one env var.
- 37 unit tests on the backend.

**Tech stack**: LangGraph · Neo4j (Text2Cypher + APOC) · `paraphrase-multilingual-MiniLM-L12-v2` · FastAPI · SSE · MySQL · Redis · Vue 3 + Pinia + Element Plus · MiniMax-M2.7 (OpenAI-compatible)

**Demo data notice**: All numeric values in the public repo are placeholders (`123`); enterprise / region names are anonymised. The repo demonstrates schema and pipeline — drop in real MRV data for production use.

**Outcome**: Reusable multi-agent GraphRAG template; the supervisor + sub-agent + grounding-judge pattern has since been reused by the team for two additional customer-service domains.

**Code**: <https://github.com/AntColony10086/ScopeGraph>
