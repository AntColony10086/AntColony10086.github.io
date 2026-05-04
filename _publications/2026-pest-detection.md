---
title: "Few-Shot Multi-Class Pest Detection via Similarity-Based Attention and Multi-Class Similarity Competition"
collection: publications
category: manuscripts
permalink: /publication/2026-pest-detection
excerpt: 'A few-shot pest-counting model with similarity-based attention, wavelet-domain co-processing, point-to-region matching loss, and a multi-class similarity-competition mechanism. MAE +8.06%, RMSE +13.09% over baseline.'
date: 2026-05-01
venue: 'Under review'
---

**Status**: Under review (first author).

**Abstract** — Cotton-field pest detection suffers from three coupled bottlenecks: (1) high annotation cost in the few-shot regime, (2) low inter-class separability between visually similar pests, and (3) very large object-scale variance. We propose a similarity-matching counting model that introduces attention along the similarity dimension to refine both feature extraction and matching, applies wavelet-domain co-processing to recover small targets, and adopts a point-to-region matching loss to stabilise training under sparse annotations. A multi-class similarity-competition head forces the model to discriminate between visually similar classes. On our multi-class few-shot benchmark, the proposed method improves MAE by **8.06%** and RMSE by **13.09%** over the strongest baseline.

**Contribution role**: First author. Method design, full experiments, paper writing.
