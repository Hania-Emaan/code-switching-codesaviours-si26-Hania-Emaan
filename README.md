# Code Switching NLP | Code Saviours SI-26 |Hania-Emaan
# Code-Mixed Roman Urdu & English Dataset

A token-level annotated dataset designed for **Language Identification**, **Token Classification**, and **Code-Mixing Analysis** in text containing Roman Urdu (Urdu written in Latin script) and English.

---

## 📌 Dataset Overview

Code-mixing between Roman Urdu and English is widely prevalent on social media, messaging platforms, and online forums across South Asia. Standard Natural Language Processing (NLP) models trained on monolingual data often struggle to process such text. 

This dataset provides word-level and sentence-level token annotations to help train and evaluate NLP models (such as BiLSTM-CRF, BERT, or XLM-RoBERTa) for sequence labeling and language identification.

- **Primary Languages:** Roman Urdu, English
- **Task Type:** Token Classification / Sequence Labeling / Language Identification
- **File Formats:** CSV 

---

## 📂 Repository Structure

```text
├── dataset.csv            # Cleaned dataset with token-level annotations
├── preprocessing.ipynb    # Python notebook used for data cleaning & encoding
└── README.md              # Dataset documentation

---
language:
- ur
- en
license: mit
tags:
- token-classification
- code-switching
- roman-urdu
- xlm-roberta
base_model: xlm-roberta-base
metrics:
- f1
pipeline_tag: token-classification
library_name: transformers
---

# Code-Switching Token Classification Model (Roman Urdu & English)

## Model Overview
This model is a fine-tuned **XLM-RoBERTa (base)** architecture trained to perform word/token-level **Language Identification** on code-mixed social text containing **Roman Urdu** and **English**.

- **Developed by:** Hania Emaan
- **Model Type:** Token Classification / Sequence Labeling
- **Base Model:** `xlm-roberta-base`
- **Languages:** Roman Urdu, English

---

## Label Scheme & Categories

| Label | Description | Example Words |
| :--- | :--- | :--- |
| **`URD`** | Roman Urdu tokens | *aaj*, *kal*, *kaam*, *hai* |
| **`ENG`** | English tokens | *project*, *submission*, *file* |
| **`MIX`** | Hybrid code-mixed tokens | Hybrid words with local inflections |

---

## Evaluation Results

The model was evaluated on a held-out test set using token-level precision, recall, and F1-scores via `seqeval`:

| Class / Label | Precision | Recall | F1-Score |
| :--- | :--- | :--- | :--- |
| **`ENG`** | 0.99 | 0.99 | **0.99** |
| **`URD`** | 0.91 | 0.89 | **0.90** |
| **`MIX`** | 0.00 | 0.00 | **0.00** |
| **Overall (Micro Avg)** | **0.98** | **0.97** | **0.97** |

---

## How to Get Started

You can load and test this model directly using Hugging Face's `pipeline`:

```python
from transformers import pipeline

nlp = pipeline(
    "token-classification", 
    model="HaniaEmaan/code-switching-codesaviours-si26-hania", 
    aggregation_strategy="simple"
)

sentence = "aaj mera project submission complete ho gaya hai"
predictions = nlp(sentence)

for pred in predictions:
    print(f"Token: {pred['word']} | Label: {pred['entity_group']} | Score: {pred['score']:.4f}")
