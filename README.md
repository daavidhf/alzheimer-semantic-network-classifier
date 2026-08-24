# Alzheimer's Classification via Semantic Networks

Graph-based classification pipeline distinguishing Alzheimer's disease patients (AD) from healthy controls (NC) using semantic-fluency data, extending the diagnostic framework of Zemla & Austerweil (2019).

> Team project — Complex Networks / Computational Neuroscience coursework (MHEDAS, URV), 3-person team.

## 🙋 My contribution — David Hidalgo Fàbregas

I built the entire unsupervised branch of the pipeline: (1) constructed per-subject semantic networks from the verbal fluency data, (2) extracted topological features from each network, (3) ran a statistical analysis to identify which features were significantly discriminative, and (4) used those features to build a **Subject Similarity Network**, which I then partitioned via community detection (Louvain, Infomap, DCSBM) to unsupervisedly separate AD from NC subjects. The **directed transition networks** and the downstream Random Forest classifier were built by the rest of the team.

## Overview

- **Cohort:** 158 subjects (97 NC / 61 AD), NACC dataset
- **Approach:** characterize semantic-network topology from verbal fluency data, statistically validated against null models (p < 0.001)
- **Two classification strategies**, both without using diagnostic labels during network construction:
  1. **Subject Similarity Network** + community detection (Louvain, Infomap, DCSBM) — up to **82% accuracy**
  2. **Directed transition networks** modeling word-retrieval dynamics, fed into a supervised Random Forest classifier — **87.3% accuracy** (Leave-One-Out Cross-Validation)

## Methodology

1. **Network construction** — semantic networks built from verbal fluency task data, one per subject
2. **Statistical validation** — network topology compared against null/random-graph models
3. **Feature extraction & significance analysis** — topological features extracted from each network, with statistical analysis identifying which features are significantly discriminative between AD and NC
4. **Unsupervised route** — those features used to build a Subject Similarity Network across all participants, partitioned via community detection algorithms (Louvain, Infomap, DCSBM) to separate AD from NC without ever using diagnostic labels in network construction
5. **Supervised route** — directed transition networks capturing retrieval dynamics, used as features for a Random Forest classifier, validated with LOOCV given the limited sample size

## Tech stack

`Python` · `NetworkX` · `scikit-learn` (Random Forest) · statistical hypothesis testing


## Reference

Zemla, J.C., & Austerweil, J.L. (2019) — the semantic network diagnostic framework this project extends.
