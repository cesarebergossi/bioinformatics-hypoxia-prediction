# Hypoxia Prediction from Single-Cancer-Cell RNA-seq Data

This project explores the potential to predict oxygen exposure levels—hypoxia (low oxygen) or normoxia (normal oxygen)—in cancer cells based solely on their gene expression profiles, using single-cell RNA sequencing (scRNA-seq) data. It was developed as part of the AI Lab course during my BSc, with a focus on real-world applications of machine learning in biomedical research.

## Motivation

Understanding how the tumor microenvironment, especially oxygen availability, influences gene expression is crucial in oncology. Hypoxic cells can become more aggressive and resistant to treatment, making early detection of such phenotypes important for effective interventions. This project aims to answer:

> Can we predict hypoxia or normoxia status from gene expression in single cancer cells?

## Data Overview

The dataset consists of breast cancer cells from two lines:

- **MCF7**: Estrogen-receptor-positive cells  
- **HCC1806**: Triple-negative breast cancer cells  

Each was profiled using two sequencing platforms:

- **SmartSeq**: High resolution, full-length transcript coverage
- **DropSeq**: Cost-effective, high-throughput, 3'-end sequencing

Each modality is available as:
- Raw unfiltered counts (SmartSeq only)
- Filtered and normalized expression matrices
- Annotated metadata with oxygen exposure (hypoxia/normoxia)

## Files in This Repo

```
MCF7_SmartS.ipynb     # Full analysis pipeline on MCF7 (SmartSeq)
MCF7_DropS.ipynb      # MCF7 analysis (DropSeq)
HCC1806_SmartS.ipynb  # HCC1806 analysis (SmartSeq)
HCC1806_DropS.ipynb   # HCC1806 analysis (DropSeq)
```

You can **view the notebooks directly in your browser** via nbviewer:

- [MCF7_SmartS.ipynb](https://nbviewer.org/github/cesarebergossi/bioinformatics-hypoxia-prediction/blob/main/MCF7_SmartS.ipynb)
- [MCF7_DropS.ipynb](https://nbviewer.org/github/cesarebergossi/bioinformatics-hypoxia-prediction/blob/main/MCF7_DropS.ipynb)
- [HCC1806_SmartS.ipynb](https://nbviewer.org/github/cesarebergossi/bioinformatics-hypoxia-prediction/blob/main/HCC1806_SmartS.ipynb)
- [HCC1806_DropS.ipynb](https://nbviewer.org/github/cesarebergossi/bioinformatics-hypoxia-prediction/blob/main/HCC1806_DropS.ipynb)

## Methodology

Each notebook follows a complete pipeline:

### 1. **Exploratory Data Analysis (EDA)**
- Quality checks on gene/cell distributions
- Dimensionality reduction (PCA, t-SNE) to visualize hypoxia clusters
- Unsupervised clustering (KMeans) for structure detection

### 2. **Data Preprocessing**
- Log-transformation and standardization
- Highly variable gene filtering
- Train-test split with held-out evaluation sets

### 3. **Supervised Learning**
- Trained models:  
  - Logistic Regression  
  - Support Vector Machines (linear/RBF)  
  - Random Forests  
- Cross-validation to tune hyperparameters

### 4. **Model Evaluation**
- Accuracy, precision, recall, and F1-score
- Confusion matrices on private test sets

### 5. **Biological Interpretation**
- Feature importance analysis
- Enrichment analysis of top-ranked genes using:
  - Hypoxia pathway markers
  - Glycolysis, mTORC1 signaling
  - Gene set overrepresentation


## Key Insights

- **Sequencing Technology Comparison**: SmartSeq generally outperformed DropSeq, likely due to lower sparsity.
- **Cell Line Comparison**: MCF7 was easier to classify than HCC1806, possibly due to dataset balance and gene expression clarity.
- **Model Performance**: Linear SVM and Logistic Regression consistently delivered strong results, sometimes reaching perfect classification on validation data.
- **Enrichment Findings**: Pathways such as glycolysis and hypoxia were overrepresented in selected gene sets, confirming biological relevance of model features.

## Notes

- **Test data is private** and not included in the repository.
- **Original scRNA-seq data** was anonymized and provided exclusively for academic use.
- This project is for educational and research purposes only.
