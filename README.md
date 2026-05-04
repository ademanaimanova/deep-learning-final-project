# Sentiment Analysis on Amazon Fine Food Reviews

**Course**: Applied Deep Learning  
**Dataset**: [Amazon Fine Food Reviews](https://www.kaggle.com/datasets/snap/amazon-fine-food-reviews) (Kaggle)  
**Task**: Binary sentiment classification (Positive / Negative)

---

## Project Overview

This project builds a complete sentiment analysis pipeline on a 30,000-review subset of the Amazon Fine Food Reviews dataset. Starting from a logistic regression baseline, the project progresses through an MLP, an LSTM/GRU model, and finally a fine-tuned BERT Transformer, with rigorous evaluation at every stage.

---

## Repository Structure

```
project-repo/
├── README.md
├── requirements.txt
├── final-report.md
├── data/
│   └── README.md          ← Dataset download instructions (no raw data committed)
├── notebooks/
│   ├── week1_eda.ipynb
│   ├── week2_baseline.ipynb
│   ├── week3_deep_learning.ipynb
│   └── week4_final_eval.ipynb
├── src/
│   ├── data_loader.py
│   ├── preprocessing.py
│   ├── baseline_models.py
│   ├── lstm_model.py
│   ├── bert_model.py
│   └── evaluate.py
├── reports/
│   ├── week-01.md
│   ├── week-02.md
│   ├── week-03.md
│   └── week-04.md
└── results/
    ├── baseline_results.csv
    ├── lstm_results.csv
    ├── bert_results.csv
    └── figures/
```

---

## Setup

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/project-repo.git
cd project-repo
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Download the dataset

See [`data/README.md`](data/README.md) for full instructions. In short:

```bash
pip install kaggle
kaggle datasets download -d snap/amazon-fine-food-reviews
unzip amazon-fine-food-reviews.zip -d data/raw/
```

### 4. Create the 30,000-review subset

```bash
python src/data_loader.py
```

This produces `data/processed/reviews_30k.csv` (15,000 positive + 15,000 negative).

---

## Models

| Model | Type | Val F1 |
|---|---|---|
| Logistic Regression | Baseline | TBD |
| MLP | Baseline | TBD |
| LSTM/GRU | Deep Learning | TBD |
| BERT (fine-tuned) | Transformer | TBD |

*(Results updated after each weekly training run)*

---

## Important Notes

- **Do not commit raw dataset files** — the full CSV is ~300 MB. Use the download script.
- The 30k subset (`reviews_30k.csv`) may be committed if it fits GitHub's 100 MB limit (~10 MB), but prefer using the script.
- All experiments were run on Google Colab (T4 GPU).
