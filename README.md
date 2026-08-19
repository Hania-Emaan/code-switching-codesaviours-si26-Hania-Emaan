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
# Code-Switching Token Classification | Identifies Roman Urdu and English words in code-mixed text

Code-mixing between Roman Urdu (Urdu written in the Latin script) and English is dominant across South Asian social media, chat applications, and online forums. Standard monolingual Natural Language Processing (NLP) tools fail to process these mixed sentences because they treat Roman Urdu as misspelled English or unknown words. This project solves that real-world problem by providing a custom token-annotated dataset alongside a fine-tuned multilingual model designed to accurately detect, parse, and classify language switching at the individual word level.

**Live Demo:** [HuggingFace Model Space](https://huggingface.co/HaniaEmaan/code-switching-codesaviours-si26-hania)

## How it Works
The system takes a sentence containing a mix of Roman Urdu and English words as input. It feeds the text into a fine-tuned XLM-RoBERTa transformer model that analyzes the contextual environment surrounding every single token. The model then performs sequence labeling to assign a specific language tag to each word, identifying whether it belongs to Roman Urdu (`URD`), English (`ENG`), or a mixed origin (`MIX`).

## Results
The model was fine-tuned over 5 epochs and evaluated using token-level precision, recall, and F1-scores via the `seqeval` framework:

| Tag / Label | Description | Precision | Recall | F1-Score |
| :--- | :--- | :--- | :--- | :--- |
| **`ENG`** | English Tokens | 0.99 | 0.99 | **0.99** |
| **`URD`** | Roman Urdu Tokens | 0.91 | 0.89 | **0.90** |
| **`MIX`** | Hybrid/Mixed Tokens | 0.00 | 0.00 | **0.00** |
| **Overall** | **Micro Average** | **0.98** | **0.97** | **0.97** |

## How to Run Locally

Install the required dependencies:
```bash
pip install transformers torch datasets seqeval
---

from transformers import pipeline

# Load fine-tuned pipeline from Hugging Face Hub
nlp = pipeline(
    "token-classification", 
    model="HaniaEmaan/code-switching-codesaviours-si26-hania", 
    aggregation_strategy="simple"
)

# Test sentence
text = "aaj mera project submission complete ho gaya hai"
predictions = nlp(text)

for pred in predictions:
    print(f"Token: {pred['word']} | Label: {pred['entity_group']} | Score: {pred['score']:.4f}")
---
 Built by: Hania Emaan | Code Saviours SI-26 | 2026

