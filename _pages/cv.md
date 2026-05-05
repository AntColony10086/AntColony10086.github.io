---
layout: archive
title: "Curriculum Vitae"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

📄 **Download** — [CV (Chinese, PDF)]({{ base_path }}/files/lujian_cv.pdf)

---

### Education

**Xinjiang University** · B.Eng. in Electronic Engineering · *2022 – 2026 (expected)*
- GPA **4.10 / 5.00** · Major rank **4 / 73** (top 5.48%)
- English: CET-4 538 / CET-6 462

### Research Interests

- Multimodal Agents (VLM + grounding + segmentation)
- Agent orchestration & tool use (LangGraph / MCP / Function Calling)
- RAG, evaluation, and human-in-the-loop annotation systems

### Selected Projects

- **[`echobox`](https://github.com/AntColony10086/echobox)** — open-source multimodal annotation agent (Apache-2.0, ⭐ 5). LangGraph + GECO2 + SAM2 exemplar detection, MCP tools, COCO / YOLO / Pascal VOC / Label Studio export · *first undergraduate member, Multimodal Information Technology Autonomous Region Research Center*
- **[`ScopeGraph`](https://github.com/AntColony10086/ScopeGraph)** — open-source multi-agent GraphRAG carbon assistant (MIT). LangGraph supervisor + 5 sub-agents over a Neo4j graph, hybrid Text2Cypher + vector retrieval, 3-layer per-tenant data isolation (JWT → state → Cypher whitelist), LLM-as-Judge grounding check, SSE streaming
- **Smart-agriculture system** — single-agent + RAG application (LangChain + YOLO inference + 三端联动)
- **Quadruped robot** — YOLOv8s + DeepLabv3 perception + first serial-link quadruped control framework in the lab

### Publications

- **Few-shot multi-class pest detection** with similarity-based attention and multi-class similarity competition. *Under review (first author).* MAE +8.06%, RMSE +13.09% over baseline.

### Awards

#### National
- ROBOCON National First Prize × 1
- ROBOCON National Second Prize × 5
- National College Electronic Design Contest, National Second Prize
- 嵌入式芯片与系统设计大赛, National Second Prize
- 中国国际大学生创新大赛, National Bronze Medal

#### Provincial
- 全国大学生数学建模竞赛 — Provincial Second Prize
- 华为 ICT 大赛 — Provincial Second Prize
- 计算机设计大赛 — Provincial Third Prize

#### Other
- 大学生创新创业项目立项 (project lead, 棉田害虫检测)
- Software copyright × 1 (智慧农业项目)

### Skills

- **Languages**: Python · C · C++ · Bash
- **DL frameworks**: PyTorch
- **CV models I've shipped**: YOLOv5 / YOLOv8, DeepLabv3, SAM 2, GroundingDINO
- **Agent stack**: LangChain · LangGraph · LlamaIndex · MCP · Function Calling · Pydantic
- **VLMs / models**: Qwen-VL, GPT-4V, InternVL (via API)
- **Vector DBs / RAG**: Neo4j (Text2Cypher + APOC) · pgvector, FAISS, Chroma · hierarchical chunking · parent-child retrieval · multilingual MiniLM embeddings
- **Eval / observability**: Ragas · LangSmith · LLM-as-Judge
- **Inference / serving**: FastAPI · WebSocket · Celery · Redis · Docker · vLLM (familiar)
- **Tooling**: Linux · Git · CI/CD · cloud deployment
- **Capability boundary**: framework orchestration / tool use / RAG / multimodal integration / inference deployment / agent orchestration · embedding-level fine-tuning (LoRA on small models). I do **not** train, pre-train, or do large-scale SFT on LLMs.

### Contact

- 💻 [github.com/AntColony10086](https://github.com/AntColony10086)
- 🌐 [antcolony10086.github.io](https://antcolony10086.github.io/)
