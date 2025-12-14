# Mini AI Pipeline Project: From Keywords to BERT 🤗

**Course:** CAS2105 (Yonsei University)  
**Author:** Seonjun Kim (2023149026)  
**Task:** Text Classification (AG News Dataset)

---

## 📖 Project Overview

This project focuses on constructing an end-to-end AI workflow to classify news headlines into four distinct categories: **World, Sports, Business, and Sci/Tech**. 

The goal is not just to achieve high accuracy, but to demonstrate the significant performance gap between a heuristic approach and modern deep learning techniques, reflecting on the trade-offs involving complexity and interpretability.

### 🎯 Objectives
- **Task:** Classify short news texts (titles + descriptions) into 4 classes.
- **Dataset:** [AG News](https://huggingface.co/datasets/ag_news) (Subset of 1,000 test examples).
- **approaches:**
  1.  **Naïve Baseline:** Keyword matching rules.
  2.  **AI Pipeline:** Pre-trained BERT model.

---

## 🛠 Methods

### 1. Naïve Baseline (Rule-based)
A simple keyword-based classifier that does not rely on machine learning parameters.
- **Mechanism:** Defines a dictionary of representative keywords for each class (e.g., "olympic" → Sports, "stock" → Business) and selects the class with the highest keyword count.
- **Pros:** Transparent, easy to debug, zero training cost.
- **Cons:** Ignores context, sentence structure, and semantics (fails on polysemy like "Apple" fruit vs. company).

### 2. AI Pipeline (BERT)
An advanced pipeline leveraging **Transfer Learning**.
- **Model:** `fabriceyhc/bert-base-uncased-ag_news` (Fine-tuned BERT base from Hugging Face).
- **Pipeline Stages:**
  1.  **Preprocessing:** Tokenization (WordPiece) & Truncation.
  2.  **Inference:** Encoding text and outputting logits.
  3.  **Post-processing:** Mapping labels to human-readable categories.

---

## 📊 Experimental Results

The experiment compared the two methods on **Accuracy** and **Weighted F1-Score**. The AI Pipeline significantly outperformed the baseline, particularly in categories with high semantic ambiguity like *Sci/Tech*.

### Overall Performance
| Method | Accuracy | F1-Score (Weighted) |
| :--- | :---: | :---: |
| **Naïve Baseline** | 0.531 | 0.525 |
| **AI Pipeline (BERT)** | **0.897** | **0.897** |

**

### Class-wise Performance (F1-Score)
| Category | Naïve Baseline | AI Pipeline (BERT) |
| :--- | :---: | :---: |
| **World** | 0.525 | 0.896 |
| **Sports** | 0.652 | **0.963** |
| **Business** | 0.516 | 0.866 |
| **Sci/Tech** | 0.407 | 0.861 |

**

> **Key Insight:** The baseline performed worst in *Sci/Tech* (F1: 0.407
