# Machine-Learning-DS675-MIMIC-Dataset-Project


This project explores patient vital signs data from the MIMIC dataset, focusing on data preprocessing, feature engineering, and clustering analysis. By leveraging techniques such as imputation, label encoding, K-Means clustering, and Principal Component Analysis (PCA), we aim to better understand underlying patterns in patient vital sign data.

## Table of Contents

1. [Project Overview](#project-overview)
2. [Data Description](#data-description)
3. [Data Preprocessing](#data-preprocessing)
   - [Handling Missing Values](#handling-missing-values)
   - [Pivoting Data by Patient ID](#pivoting-data-by-patient-id)
   - [Imputation](#imputation)
   - [Feature Encoding](#feature-encoding)
4. [Clustering Analysis](#clustering-analysis)
   - [K-Means Clustering](#k-means-clustering)
   - [Challenges in Clustering](#challenges-in-clustering)
5. [Dimensionality Reduction](#dimensionality-reduction)
   - [Principal Component Analysis (PCA)](#principal-component-analysis-pca)
6. [Results & Observations](#results--observations)
7. [Repository Structure](#repository-structure)
8. [How to Run](#how-to-run)
9. [Dependencies & Requirements](#dependencies--requirements)
10. [Future Work](#future-work)
11. [License](#license)
12. [Acknowledgments](#acknowledgments)

---

## Project Overview

This project investigates a subset of the MIMIC dataset (Medical Information Mart for Intensive Care) for understanding patterns in patient vital signs. The main goals are:

- To clean and preprocess the raw medical data, ensuring a robust dataset for modeling.
- To apply clustering techniques (specifically K-Means) to uncover patient groups based on their vital signs.
- To handle extensive missing values through systematic imputation.
- To reduce data dimensionality via PCA, improving cluster segregation and interpretability.

---

## Data Description

The dataset is derived from the MIMIC repository, which contains critical care patient data. The data includes various patient vitals and demographic information over multiple time points. Each patient has multiple entries, corresponding to different vital sign measurements.

Key characteristics of the data:
- **Patient ID**: A unique identifier for each patient (164 patients in total).
- **Vital Signs**: Multiple measurements (e.g., heart rate, blood pressure, respiratory rate, etc.) recorded at different time intervals.
- **Demographics/Admission Info**: Includes patient gender, admission type, and possibly other categorical attributes.
  
Due to data privacy regulations, the actual dataset source and access details (MIMIC) are assumed to be known or obtained by users with appropriate credentials.

---

## Data Preprocessing

### Handling Missing Values

The original dataset contained a large fraction of missing values:
- Any column with more than 50% missing values was dropped.
- For rows with less than 10% missing values, we performed imputation rather than dropping the entire row. This approach avoids losing critical patient information.
  
### Pivoting Data by Patient ID

Since each patient has multiple vital sign recordings over time, the data was pivoted such that each patient’s observations are presented in a single row structure. After pivoting:
- Each row represents one patient.
- Columns represent different vital measurements taken at various time points (or aggregated statistics).

This transformation allowed us to analyze each patient holistically, rather than dealing with multiple rows per patient.

### Imputation

Given the importance of patient vitals, dropping missing values was not appropriate. Instead, we used imputation techniques (e.g., mean, median, or another suitable statistical measure) to fill in missing values. The imputation helped maintain a complete dataset for each patient, but introduced the challenge that the dataset might become too "smoothed."
  
### Feature Encoding

Categorical variables such as **Gender** and **Admission Type** were label encoded. For example:
- Male/Female encoded as numerical values.
- Admission types (e.g., Emergency, Elective) encoded into integers.

This step ensured that all features were numeric and suitable for clustering algorithms such as K-Means.

---

## Clustering Analysis

### K-Means Clustering

The initial approach to identify patterns was to apply K-Means clustering. The idea was to group patients into clusters based on their vital sign profiles, hoping that distinct patient types or conditions would emerge.

### Challenges in Clustering

Due to extensive imputation and the nature of the data, the initial clustering attempts did not yield well-separated groups. The high dimensionality and the uniformity introduced by imputation made it challenging for K-Means to form meaningful, distinct clusters.

---

## Dimensionality Reduction

### Principal Component Analysis (PCA)

To address the issues encountered during clustering, we applied PCA to reduce the dataset’s dimensionality. By projecting the data onto principal components:
- We reduced noise and redundancy.
- Made the underlying structure more evident.
- Enhanced cluster formation and separation.

After PCA, the clusters became more segregated, providing better insights into patient groupings.

---

## Results & Observations

- **Before PCA**: K-Means clusters were not well-defined, likely due to high dimensionality and heavy imputation.
- **After PCA**: Clusters were more distinguishable, suggesting that dimensionality reduction can help uncover more meaningful patterns in medical data.
- **Insights**: While not definitive clinical groupings, these clusters might guide further investigation, highlight the need for more granular data, or suggest relevant subsets of features that drive patient similarity.

---

## Repository Structure
```
Machine-Learning-DS675-MIMIC-Dataset-Project/
│
├── data/
│   ├── raw_data.csv           # Original (or sample) data file
│   └── processed_data.csv     # Cleaned and pivoted dataset
│
├── notebooks/
│   ├── 01_patient_clustering.ipynb
│   ├── 02_classification.ipynb
│
│
└── README.md                  # This README file
```
