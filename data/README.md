# Data Directory

**Do not commit raw dataset files to this repository.**

The full Amazon Fine Food Reviews CSV (~300 MB) exceeds GitHub's recommended file size limit. Follow the instructions below to download and prepare the data locally or on Colab.

---

## Dataset Information

| Field | Detail |
|---|---|
| Name | Amazon Fine Food Reviews |
| Source | [Kaggle](https://www.kaggle.com/datasets/snap/amazon-fine-food-reviews) |
| Total reviews | ~568,000 |
| Subset used | 30,000 (15,000 positive, 15,000 negative) |
| Input | Review text (`Text` column) |
| Target | Binary label derived from `Score`: 1–2 → Negative (0), 4–5 → Positive (1) |
| Reviews with Score=3 | Excluded (neutral / ambiguous) |
| License | CC0: Public Domain |

---

## Download Instructions

### Option A — Kaggle CLI (recommended)

```bash
# Install Kaggle API
pip install kaggle

# Place your kaggle.json in ~/.kaggle/ (download from your Kaggle account settings)
mkdir -p ~/.kaggle
cp /path/to/kaggle.json ~/.kaggle/kaggle.json
chmod 600 ~/.kaggle/kaggle.json

# Download and unzip
kaggle datasets download -d snap/amazon-fine-food-reviews
unzip amazon-fine-food-reviews.zip -d data/raw/
```

### Option B — Manual download

1. Go to https://www.kaggle.com/datasets/snap/amazon-fine-food-reviews
2. Click **Download** (requires a free Kaggle account)
3. Unzip and place `Reviews.csv` inside `data/raw/`

### Option C — Google Colab

```python
# Run this cell at the top of any notebook
from google.colab import files
# Upload your kaggle.json when prompted
files.upload()

import os
os.makedirs('/root/.kaggle', exist_ok=True)
os.system('cp kaggle.json /root/.kaggle/')
os.system('chmod 600 /root/.kaggle/kaggle.json')
os.system('pip install -q kaggle')
os.system('kaggle datasets download -d snap/amazon-fine-food-reviews')
os.system('unzip -q amazon-fine-food-reviews.zip')
```

---

## Create the 30,000-Review Subset

After downloading `Reviews.csv`, run:

```bash
python src/data_loader.py
```

This script:
1. Loads `Reviews.csv`
2. Drops Score=3 (neutral) reviews
3. Maps Score 1–2 → label 0 (Negative), Score 4–5 → label 1 (Positive)
4. Samples 15,000 from each class (random_state=42 for reproducibility)
5. Saves to `data/processed/reviews_30k.csv`

---

## Directory Structure (after setup)

```
data/
├── README.md           ← This file (committed to GitHub)
├── raw/
│   └── Reviews.csv     ← NOT committed (download manually)
└── processed/
    └── reviews_30k.csv ← Balanced 30k subset (may be committed if <100 MB)
```
