# Code Switching NLP | Code Saviours SI-26 |Hania-Emaan
# Code-Mixed Roman Urdu & English Dataset

A token-level annotated dataset designed for **Language Identification**, **Token Classification**, and **Code-Mixing Analysis** in text containing Roman Urdu (Urdu written in Latin script) and English.

---

## 📌 Dataset Overview

Code-mixing between Roman Urdu and English is widely prevalent on social media, messaging platforms, and online forums across South Asia. Standard Natural Language Processing (NLP) models trained on monolingual data often struggle to process such text. 

This dataset provides word-level and sentence-level token annotations to help train and evaluate NLP models (such as BiLSTM-CRF, BERT, or XLM-RoBERTa) for sequence labeling and language identification.

- **Primary Languages:** Roman Urdu, English
- **Task Type:** Token Classification / Sequence Labeling / Language Identification
- **File Formats:** CSV / JSON

---

## 📂 Repository Structure

```text
├── dataset.csv            # Cleaned dataset with token-level annotations
├── preprocessing.ipynb    # Python notebook used for data cleaning & encoding
└── README.md              # Dataset documentation
