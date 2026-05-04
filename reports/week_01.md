# Week 1 Progress Report

**Project:** Sentiment Analysis on Amazon Fine Food Reviews  
**Phase:** Week 1 — Data Understanding & Exploratory Data Analysis  
**Timeline:** 4-week NLP pipeline  
**Status:** Completed  
**Last Updated:** May 2026  

---

# 1. Project Summary

This project focuses on building a sentiment classification system for Amazon Fine Food Reviews using Natural Language Processing techniques and deep learning models.

The objective is to classify reviews into two categories:

- Positive sentiment  
- Negative sentiment  

The system is designed as a text classification pipeline for analyzing customer feedback at scale.

---

# 2. Work Completed This Week

## 2.1 Repository Setup

The project structure was initialized and organized into modular components:

- README.md — project overview  
- requirements.txt — dependencies  
- src/ — source code modules  
- notebooks/ — exploratory and experimental notebooks  
- reports/ — weekly reports  
- results/ — outputs and figures  

---

## 2.2 Dataset Preparation

Dataset used: Amazon Fine Food Reviews (Kaggle)

- Original dataset size: ~568,454 reviews  
- Labeling:
  - Score > 3 → Positive (1)
  - Score ≤ 3 → Negative (0)

A balanced subset was created for training:

- 30,000 total samples  
- 15,000 positive  
- 15,000 negative  

This approach improves training efficiency and reduces computational cost while maintaining class balance.

---

## 2.3 Data Loading Pipeline

A custom data loader was implemented in src/data_loader.py to:

- Load raw dataset  
- Filter and clean data  
- Exclude neutral reviews (Score = 3)  
- Generate balanced subset  
- Ensure reproducibility with fixed random seed  

---

## 2.4 Exploratory Data Analysis

EDA was performed in week1_eda.ipynb and included:

- Distribution of review scores in full dataset  
- Class balance analysis in subset  
- Review length distribution (word and character level)  
- Identification of long-tail distributions  
- Top frequent words after preprocessing  
- Manual inspection of sample reviews  

---

## 3. Dataset Statistics

| Metric | Value |
|------|------|
| Total reviews | 568,454 |
| Filtered dataset (Score ≠ 3) | ~525,814 |
| Final working dataset | 30,000 |
| Positive samples | 15,000 |
| Negative samples | 15,000 |
| Average words (positive) | ~82 |
| Average words (negative) | ~74 |
| Median review length | ~54 words |

---

## 4. Outputs Generated

The following figures were produced during EDA:

- score_distribution.png — rating distribution  
- text_length_distribution.png — review length analysis  
- top_words.png — most frequent words per class  

---

## 5. Issues and Notes

No major issues were encountered during this phase.

The main consideration was computational efficiency due to dataset size, which was addressed by sampling a balanced subset.

The raw dataset is not included in the repository and is excluded via .gitignore.

---

## 6. Next Steps

Week 2 will focus on model development:

- Implementation of text preprocessing pipeline  
- TF-IDF feature extraction  
- Baseline models:
  - Logistic Regression  
  - Multilayer Perceptron  

- Train/validation/test split (70/15/15)  
- Model evaluation using accuracy, precision, recall, and F1-score  
- Saving baseline results and evaluation figures
