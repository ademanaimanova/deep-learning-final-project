# Sentiment Analysis on Amazon Fine Food Reviews

## Author
Naimanova Adema

---

## 1. Overview

This project focuses on the task of **binary sentiment classification** using textual data from Amazon product reviews. The objective is to automatically determine whether a given review expresses a **positive or negative sentiment**.

Sentiment analysis is a fundamental problem in natural language processing (NLP) with practical applications in recommendation systems, customer feedback analysis, and market research. This project demonstrates how both classical machine learning and modern deep learning approaches can be applied to solve this problem.

The project follows a structured workflow including dataset preparation, exploratory data analysis, baseline modeling, deep learning implementation, evaluation, and result interpretation.

---

## 2. Problem Statement

The rapid growth of e-commerce platforms has led to an overwhelming volume of user-generated content in the form of product reviews. These reviews contain valuable information about customer satisfaction, product quality, and overall user experience. However, manual analysis of such large-scale textual data is inefficient.

This project addresses the problem of **automatic sentiment classification** of textual reviews. The goal is to classify Amazon food product reviews into **positive and negative categories** based on their text.

The task is formulated as a **binary text classification problem**, where:
- Input: review text  
- Output: sentiment label (positive / negative)

---

## 3. Dataset

The dataset used in this project is the **Amazon Fine Food Reviews** dataset from Kaggle.

### Dataset details:
- Total samples: 30,000 reviews  
- Positive: 15,000  
- Negative: 15,000  
- Type: Text data (user reviews)

### Input / Output:
- Input: review text  
- Output: sentiment label  

### Notes:
- Balanced dataset is used to avoid class imbalance  
- Dataset is not stored in the repository due to size limitations  
- Download instructions are provided in `data/README.md`

Dataset source:  
https://www.kaggle.com/datasets/snap/amazon-fine-food-reviews

---

## 4. Repository Structure
project-repo/
├── README.md
├── data/
│ └── README.md
├── notebooks/
├── src/
├── reports/
│ ├── week-01.md
│ ├── week-02.md
│ ├── week-03.md
│ └── week-04.md
├── results/
├── requirements.txt
└── final-report.md

### Description:
- `data/` – dataset instructions and storage guide  
- `notebooks/` – EDA and experiments  
- `src/` – training, preprocessing, evaluation code  
- `reports/` – weekly progress reports  
- `results/` – plots, metrics, outputs  
- `requirements.txt` – dependencies  
- `final-report.md` – final analysis report  

---

## 5. Prerequisites

- Python 3.9+  
- pip  
- Jupyter Notebook (optional for local run)  
- Google Colab (optional alternative)  
- ~5–10 GB storage  

---

## 6. Installation

Step 2: Create virtual environment
python -m venv venv
Step 3: Activate environment
venv\Scripts\activate
Step 4: Install dependencies
pip install -r requirements.txt

## 7. Dataset Setup
Download dataset from Kaggle
Extract files
Place them in data/ directory
Follow instructions in data/README.md

## 8. Weekly Breakdown
Week 1: Data Preparation & EDA
Dataset loading
Data cleaning
Text preprocessing
Exploratory Data Analysis
Train/test split
Week 2: Baseline Models
TF-IDF feature extraction
Logistic Regression
MLP model
Baseline evaluation
Week 3: Deep Learning Models
LSTM / GRU models
Embedding layers
BERT fine-tuning
Model comparison
Week 4: Final Evaluation
Confusion matrix
Error analysis
Model comparison
Final report preparation
## 9. Technologies Used
Category	Tools
Deep Learning	PyTorch / TensorFlow
NLP	NLTK / spaCy / Hugging Face Transformers
Data Science	NumPy, Pandas, Scikit-learn
Visualization	Matplotlib, Seaborn
Utilities	tqdm, joblib
Development	Jupyter Notebook, Google Colab
Version Control	Git, GitHub

## 10. Running the Project
Local:
jupyter notebook
python src/train.py
python src/evaluate.py
Google Colab:
Open notebook in Colab
Upload dataset or connect Drive
Run cells sequentially
Enable GPU if needed
## 11. License

This project is for educational purposes only.
Dataset is used under Kaggle license.
