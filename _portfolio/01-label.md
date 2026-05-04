---
title: "label · Active Multimodal Annotation Agent"
excerpt: "A LangGraph-orchestrated multimodal agent for human-in-the-loop visual annotation, combining Qwen-VL + GroundingDINO + SAM 2 with active learning.<br/><img src='/images/proj-label.png' style='max-width:520px'>"
collection: portfolio
date: 2024-10-01
permalink: /portfolio/label/
---

**Role**: Core member (first undergraduate) of the Xinjiang Multimodal Information Technology Autonomous Region Research Center · 2024.10 – 2026.04

**One-liner**: A reproducible multimodal agent platform that turns long-tail visual annotation from a human bottleneck into a human-in-the-loop pipeline.

**Why this exists**: Several CV / multimodal / remote-sensing projects in the lab share the same bottleneck — high annotation cost, weak zero-shot ability on long-tail classes, and no unified interface across image / video. We needed a shared infrastructure rather than another one-off labelling tool.

**System design**

```
[Image / Video]
     ↓
[Concept Agent]            ← Qwen-VL: generate concept prompts
     ↓
[Open-Vocabulary Detector] ← GroundingDINO: locate candidates
     ↓
[Pixel / Video Segmentor]  ← SAM 2: mask + cross-frame tracking
     ↓
[Uncertainty Scoring]      ← VLM consistency vote + SAM 2 mask score
     ↓
[Active-Learning Router]   ← BALD / Core-set: route the most useful samples to humans
     ↓
[Human-in-the-loop UI]
```

**My contribution**

- LangGraph state-machine orchestration across the five-stage pipeline
- MCP-style tool wrapping so other lab projects can consume the same agents
- BALD / Core-set active-learning policies for sample selection
- FastAPI + Celery + Redis async workers; LangSmith trace for every agent step
- Pydantic-validated structured outputs throughout

**Tech stack**: LangGraph · Qwen-VL · GroundingDINO · SAM 2 · MCP · FastAPI · Celery · Redis · LangSmith · Pydantic

**Status / metrics** *(numbers being finalised — `TBD` to be replaced as benchmarks land)*

| Metric | Value |
| --- | --- |
| Annotation-time reduction vs manual | TBD |
| mAP on benchmark subset | TBD |
| BALD vs Core-set vs Random ablation (AUC over labelling budget) | TBD |
| End-to-end p95 latency per image | TBD |

**Outcome**: First multimodal active-annotation agent platform in the research centre; already adopted by **two internal projects** (including my own few-shot pest-detection 大创).

**Code**: <https://github.com/AntColony10086/label>
