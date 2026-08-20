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

**Live Demo:** [HuggingFace Model Space](https://huggingface.co/spaces/HaniaEmaan/Code-Switching-Demo)

**Demo video:** [Video](https://www.loom.com/share/000cbb93c88c418dadfadc105ad46960)

## How it Works
The system takes a sentence containing a mix of Roman Urdu and English words as input. It feeds the text into a fine-tuned XLM-RoBERTa transformer model that analyzes the contextual environment surrounding every single token. The model then performs sequence labeling to assign a specific language tag to each word, identifying whether it belongs to Roman Urdu (`URD`), English (`ENG`), or a mixed origin (`MIX`).

## Evaluation & Model Performance

The model was evaluated using `seqeval` on a code-switched token classification test set.

| Tag / Label | Description | Precision | Recall | F1-Score | Support |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **`ENG`** | English Tokens | 0.93 | 0.94 | **0.93** | 83 |
| **`MIX`** | Hybrid/Mixed Tokens | 1.00 | 0.62 | **0.76** | 13 |
| **`URD`** | Roman Urdu Tokens | 0.62 | 0.62 | **0.62** | 13 |
| **Micro Avg** | Overall Token Level | 0.90 | 0.86 | **0.88** | 109 |
| **Macro Avg** | Class Unweighted Avg | 0.85 | 0.72 | **0.77** | 109 |
| **Weighted Avg** | Class Weighted Avg | **0.90** | **0.86** | **0.88** | **109** |

### Key Summary
* **Token-Level Accuracy:** **90.83%**
* **Validation Loss:** **0.2721**
* **Base Architecture:** `XLM-RoBERTa-base` fine-tuned for 12 epochs.
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

