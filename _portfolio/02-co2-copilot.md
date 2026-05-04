---
title: "co2-copilot · Multi-Agent Carbon Accounting Assistant"
excerpt: "A four-layer LangGraph multi-agent system (router → domain experts → aggregator → judge) for IPCC-compliant carbon accounting Q&A.<br/><img src='/images/proj-co2copilot.png' style='max-width:520px'>"
collection: portfolio
date: 2024-09-01
permalink: /portfolio/co2-copilot/
---

**Role**: Core member · 2024.09 – 2025.04
**Repo (legacy name, will be renamed `co2-copilot`)**: <https://github.com/AntColony10086/AIconverstionSys>

**One-liner**: Carbon-accounting consultancy is policy-heavy, formula-heavy, and data-heavy. A single LLM hallucinates; a single retrieval misses scope; a brittle prompt drifts. The fix is to decompose the conversation into a small graph of specialists with a judge on top.

**Architecture**

```
[user query]
      ↓
[Router Agent]            ← 5-way intent classification
      ↓
[Policy RAG] [Calc Tools] [Mitigation Agent]
LlamaIndex+pgvector   Function Calling      LLM + KB
      ↓                                         ↓
[Aggregator Agent]        ← merge expert outputs
      ↓
[Judge Agent]             ← LLM-as-Judge: faithfulness + completeness; route to human if low-confidence
```

**My contribution**

- LangGraph four-layer state machine (router → experts → aggregator → judge)
- LlamaIndex + pgvector hierarchical RAG over IPCC Guidelines, GB/T 32150, and other regulations, chunked at the *chapter–section–clause* granularity with parent-child retrieval
- 10+ Function-Calling tools wrapping IPCC emission factors and per-scenario formulas (electricity, coal, transport, ...)
- LLM-as-Judge for faithfulness + completeness scoring; low-confidence answers escalate to humans
- FastAPI + WebSocket + Redis for multi-turn session state
- Ragas offline evaluation on Faithfulness and Answer Relevancy

**Tech stack**: LangGraph · LlamaIndex · pgvector · Function Calling · FastAPI · WebSocket · Redis · Ragas · LangSmith

**Status / metrics** *(numbers being finalised)*

| Metric | Value |
| --- | --- |
| RAGAS Faithfulness | TBD |
| RAGAS Answer Relevancy | TBD |
| Tool-call success rate | TBD |
| Hallucination rate (judged) | TBD |
| Latency p50 / p95 | TBD |
| Cost per query | TBD |

**Outcome**: Reusable carbon-accounting customer-service agent stack; the multi-agent template has since been reused by the team for two additional customer-service domains.
