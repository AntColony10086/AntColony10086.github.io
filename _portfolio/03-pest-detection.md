---
title: "Few-Shot Pest Detection · First-Author Paper (under review)"
excerpt: "A few-shot pest-counting model with similarity-based attention, wavelet-domain co-processing, and a multi-class similarity-competition head.<br/><img src='/images/proj-pest-detection.png?v=2' style='max-width:520px'>"
collection: portfolio
date: 2025-04-01
permalink: /portfolio/pest-detection/
---

**Role**: Project lead (大创负责人) · 2025.04 – 2026.04 · *Paper under review (first author).*

**Why this exists**: Cotton-field pest detection has three structural problems — high annotation cost, low inter-class separability between visually similar pests, and very large object-scale variance (a few pixels to tens of pixels). A standard counting model overfits each of those failure modes individually.

**Method**

- **Backbone**: similarity-matching counter
- **Attention on the similarity dimension** — refines feature extraction *and* the matching itself
- **Wavelet-domain co-processing** — recovers small targets that vanilla feature pyramids lose
- **Point-to-region matching loss** — stabilises training under sparse few-shot annotation
- **Multi-class similarity-competition head** — forces the model to discriminate between visually-similar pest classes rather than averaging them

**Result**

| Metric | Δ vs baseline |
| --- | --- |
| MAE | **+8.06%** |
| RMSE | **+13.09%** |

State-of-the-art on the same task in our comparison. Code + reproducible experiments will be released alongside the camera-ready.

**Tech stack**: PyTorch · attention mechanisms · wavelet transforms · point-to-region losses · few-shot learning

**Outcome**: National 大创 立项 (project-level grant); paper currently under review.
