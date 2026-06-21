# Not All Negatives Are Equal: LLM-based Negative Sample Verification for Drug-Drug Interaction Prediction

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![Conference](https://img.shields.io/badge/CIKM-2026-brightgreen.svg)](https://www.cikmconference.org/)

Official repository for the paper **"Not All Negatives Are Equal: LLM-based Negative Sample Verification for Drug-Drug Interaction Prediction"** (CIKM 2026).

## 📌 Overview
Drug-Drug Interactions (DDIs) pose a direct threat to patient safety. Existing Knowledge Graph (KG)-based DDI prediction models typically rely on random negative sampling under the Local Closed-World Assumption (LCWA). However, this introduces the **Positive-Unlabeled (PU) problem**, where unverified drug pairs are mislabeled as negatives, acting as noise in the training signal.

This repository provides an **LLM-based negative sample verification framework** that leverages pharmacological reasoning (Pharmacokinetics/Pharmacodynamics) to construct highly reliable negative datasets through iterative resampling. By filtering out PU noise, this framework significantly improves the reliability and downstream performance (AUPR, AUROC) of DDI prediction models like TIGER.

## ⚙️ Framework Pipeline
Our pipeline consists of five main steps:
1. **Candidate Queue Initialization:** Excludes known positive pairs and prepares a Valid Drug Pool.
2. **LLM Prompting and Scoring:** Evaluates the probability of no interaction using LLMs (Gemini Flash-Lite, GPT-4o-mini) via structured prompting (Zero-shot, CoT, Self-Consistency).
3. **Filtering and Acceptance Decision:** Accepts pairs with a probability $\ge 0.7$ as verified negatives.
4. **Iterative Resampling:** Replaces rejected samples with newly generated candidate pairs from the KG.
5. **Final Dataset Construction:** Outputs the verified negative dataset for downstream model training.

## 📂 Repository Contents
* `drugbank_final.ipynb`: Implementation of the LLM-based verification pipeline (Gemini Flash-Lite and GPT-4o-mini) and final verified negative dataset generation for the **DrugBank** dataset.
* `KEGG_final.ipynb`: Implementation of the LLM-based verification pipeline (Gemini Flash-Lite and GPT-4o-mini) and final verified negative dataset generation for the **KEGG** dataset.

## 🚀 Getting Started

### Datasets
* **DrugBank:** Widely used benchmark for DDI prediction.
* **KEGG:** Biological relationship information at the metabolic pathway level.
