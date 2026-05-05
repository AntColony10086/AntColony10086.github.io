---
title: "echobox agent"
excerpt: "One box → all the boxes. A LangGraph-driven multimodal annotation agent: draw one bbox, an LLM-supervised exemplar detector (GECO2 + SAM2) returns every similar object. Workbench + Viewer in one app, MCP tools for other agents.<br/><img src='/images/proj-label.png?v=3' style='max-width:520px'>"
collection: portfolio
date: 2024-10-01
permalink: /portfolio/echobox/
redirect_from:
  - /portfolio/label/
---

**Role**: Author / maintainer · core member (first undergraduate) of the Xinjiang Multimodal Information Technology Autonomous Region Research Center · 2024.10 – present

**Repo**: <https://github.com/AntColony10086/echobox> · Apache-2.0 · ⭐ 5

**One-liner**: Long-tail visual annotation is the bottleneck across most of our lab's CV / multimodal / remote-sensing projects. Echobox turns it from "label every box by hand" into "draw one box, accept the rest" — and exposes the same tools as MCP so other agents can drive annotation programmatically.

**What it does**

- **Workbench**: full agent-driven annotation. Draw one exemplar bbox; an LLM-supervised exemplar detector ([GECO2](https://github.com/jerpelhan/GECO2), backed by Meta's [SAM2](https://github.com/facebookresearch/sam2)) returns every similar object in the image. Adjust → accept → save.
- **Viewer**: a zero-dependency offline preview of YOLO / point annotations.
- **LangGraph agent** handles the boring parts: folder scanning, train/val/test split, label suggestion, dataset export to **COCO / YOLO / Pascal VOC / Label Studio JSON**.
- **MCP server**: same tools exposed over MCP stdio so Claude Code / Cursor / other agents can drive annotation programmatically.

**System design**

```
Browser ──▶ frontend (Vite, :5173)
                │
                ▼
          app (FastAPI, :8000) ──▶ ml_backend (FastAPI + GPU, :9090)
                │                         │
                │                         └─▶ GECO2 / SAM2 inference
                │
                ├─▶ OpenAI-compatible LLM (DashScope / MiniMax / OpenAI / …)
                └─▶ SQLite + filesystem workspace

mcp_server (stdio) ──▶ app HTTP — for Claude Code / Cursor consumers
```

Four processes, all local — **no Docker required**.

**My contribution**

- Authored the whole project end-to-end: LangGraph state-machine orchestration, FastAPI app + ml_backend split, React + Vite + react-konva frontend, MCP server.
- Wrapped GECO2 (a counter) as a *detector*: binarise the predicted heatmap → bboxes → return as exemplar matches.
- Multi-provider LLM layer with structured-output fallback (`json_schema` → `function_calling` → manual JSON parse) so it works against MiniMax / DashScope / OpenAI without code changes.
- Full export pipeline (COCO / YOLO / Pascal VOC / Label Studio JSON) with consistent train/val/test split.

**Tech stack**: LangGraph · GECO2 · SAM2 · FastAPI · React + Vite + react-konva · MCP · SQLite · OpenAI-compatible LLM (DashScope / MiniMax / OpenAI)

**Outcome**

- First multimodal annotation-agent platform in the research centre; adopted by **two internal projects** (including my own few-shot pest-detection 大创).
- Open-sourced under Apache-2.0; ⭐ 5 on GitHub at time of writing.

**Code**: <https://github.com/AntColony10086/echobox>
