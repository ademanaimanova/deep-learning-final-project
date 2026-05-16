# Week 3 Progress Report

**Project**: Sentiment Analysis on Amazon Fine Food Reviews  
**Date**: Week 3  

---

## What Was Completed This Week

1. **BiLSTM and BiGRU models** (`src/lstm_model.py`):
   - Word-level tokenisation with `SimpleTokenizer` (vocab=30k, max_len=200)
   - Embedding layer: 128-dim, random initialisation
   - 2-layer Bidirectional LSTM / GRU with hidden_dim=256
   - Dropout=0.3 on embeddings and final hidden state
   - Training: Adam lr=1e-3, BCE-with-logits loss, gradient clipping (max_norm=1.0)
   - LR scheduler: `ReduceLROnPlateau` with patience=2, factor=0.5
   - Early stopping patience=3

2. **BERT fine-tuning** (`src/bert_model.py`):
   - Model: `bert-base-uncased` (110M parameters)
   - Tokenisation: WordPiece, max_len=128
   - Optimiser: AdamW, lr=2e-5, weight_decay=0.01
   - Scheduler: linear warmup (10% of steps) → linear decay
   - Epochs: up to 4 with early stopping patience=2
   - Trained on Google Colab T4 GPU (~22 min/epoch)

3. **Error analysis**: extracted 10 BERT misclassifications per error type and saved to `results/bert_error_analysis.csv`.

4. **Notebook**: `notebooks/week3_deep_learning.ipynb` with full training loops, loss curves, confusion matrices.

---

## Important Commits This Week

| Commit Message | Files Changed |
|---|---|
| `add: SimpleTokenizer and sequence encoding` | `src/preprocessing.py` |
| `add: BiLSTM model architecture and training loop` | `src/lstm_model.py` |
| `add: BiGRU model and loss curve plots` | `src/lstm_model.py`, `results/figures/` |
| `add: BERT fine-tuning script with warmup scheduler` | `src/bert_model.py` |
| `add: BERT training on Colab T4 — loss curves saved` | `results/figures/bert_loss_curve.png` |
| `add: error analysis on BERT misclassifications` | `results/bert_error_analysis.csv` |
| `add: week-03 report` | `reports/week-03.md` |

---

## Model Results (Test Set)

| Model | Accuracy | Precision | Recall | F1-Score | Training Time |
|---|---|---|---|---|---|
| BiLSTM | ~0.921 | ~0.923 | ~0.919 | ~0.921 | ~8 min (Colab T4) |
| BiGRU | ~0.919 | ~0.920 | ~0.918 | ~0.919 | ~7 min (Colab T4) |
| BERT | **~0.952** | **~0.954** | **~0.950** | **~0.952** | ~90 min (Colab T4) |


**Key observations**:
- BERT significantly outperforms all other models (~4% F1 improvement over BiLSTM), demonstrating the value of pretraining on large corpora and contextual representations.
- BiLSTM marginally outperforms BiGRU (~0.2% F1), consistent with LSTM's ability to retain longer-range dependencies.
- Both RNN models outperform the TF-IDF baselines, confirming that sequential context matters for food review sentiment.

---

## Error Analysis — BERT

**False Negatives (positive reviews predicted as negative)**:
- Reviews containing sarcasm or ironic praise: e.g., *"Not what I expected but oddly addictive"* — mixed phrasing confuses the model.
- Positive reviews that start with a complaint: e.g., *"Shipping was terrible... but the product itself is wonderful."*

**False Positives (negative reviews predicted as positive)**:
- Politely worded complaints: e.g., *"I was hoping this would be better. The quality is not quite there."* — lacks strong negative signal words.
- Reviews comparing unfavourably to another product: context-dependent negation.

---

## Figures Generated

- `results/figures/bilstm_loss_curve.png`
- `results/figures/bigru_loss_curve.png`
- `results/figures/bert_loss_curve.png`
- `results/figures/bilstm_confusion.png`
- `results/figures/bigru_confusion.png`
- `results/figures/bert_confusion.png`

---

## Problems / Blockers

- BERT fine-tuning required reducing `batch_size` from 64 to 32 to fit within Colab T4 VRAM (16 GB). Training time increased accordingly.
- BiLSTM with max_len=200 and batch=64 occasionally runs out of RAM on CPU. GPU (Colab) resolves this.

---

## Plan for Week 4

- Consolidate all results into `results/all_model_results.csv`.
- Produce final comparison charts (`evaluate.py`: `compare_models`, heatmap).
- Write `final-report.md` (all 12 sections).
- Finalise `week-04.md` report.
- Ensure repository is clean: no large raw files, clear README, all notebooks runnable.
- Prepare 5-7 minute presentation slides.
