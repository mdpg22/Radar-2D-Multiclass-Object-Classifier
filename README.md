# 📡 Radar-Based Multiclass Object Classification (2D Radar)

Industrial Machine Learning project focused on building a multiclass
object classifier using 2D radar detection data.

------------------------------------------------------------------------

## 🎯 Project Objective

The goal of this project is to develop a multiclass classifier capable
of identifying different object types based on radar detection features.

The classification task includes the following object classes:

-   Car (0)
-   Large vehicle (1)
-   Truck (2) → merged into Large vehicle (1)
-   Bus (3) → merged into Large vehicle (1)
-   Bicycle (5)
-   Person (7)
-   Group of people (8) → merged into Person (7)
-   Other dynamic object (10)
-   Static background (11)

The objective is to:

-   Train a multiclass classifier
-   Evaluate performance using Average Precision (AP) per class
-   Compute mean Average Precision (mAP)
-   Analyze model behavior at different ranges and azimuth angles
-   Define an operating threshold prioritizing precision for the
    "Person" class

------------------------------------------------------------------------

## 📂 Dataset Description

Each radar detection is treated as an independent object (problem
simplification).

### Target Variable (y)

Object class label (multiclass problem)

### Feature Variables (X)

-   `range_sc` → radial distance \[m\]
-   `azimuth_sc` → azimuth angle \[rad\]
-   `radar_cross_section` → RCS \[dBsm\]
-   `radial_velocity` → radial velocity \[m/s\]
-   `vr_compensated` → ego-motion compensated radial velocity \[m/s\]
-   `x_cc`, `y_cc` → relative Cartesian coordinates \[m\]
-   `x_seq`, `y_seq` → global Cartesian coordinates \[m\]

Note: Detection reliability decreases at large azimuth angles.

------------------------------------------------------------------------

## 🛠 Technologies Used

-   Python / R
-   pandas / tidyverse
-   scikit-learn
-   numpy
-   matplotlib / seaborn
-   Precision-Recall analysis tools

------------------------------------------------------------------------

## 🔎 Project Structure

radar-multiclass-object-classification/ 
│ 
├── Entrega_2.ipynb #Main code of analysis
├── Entregable2.RData #Dataset
├── 2025_Entregable2_Clasificador_Multiclase.pdf #Information and documentation
└── README.md

------------------------------------------------------------------------

## 📊 Methodology

### 1️⃣ Data Preparation

-   Load RData dataset
-   Reassign labels:
    -   Bus (3) and Truck (2) → Large vehicle (1)
    -   Group of people (8) → Person (7)
-   Split dataset:
    -   Training → first 200k detections
    -   Validation → next 200k detections

------------------------------------------------------------------------

### 2️⃣ Exploratory Radar Analysis

-   Analyze RCS median ± MAD
-   Compare RCS distribution between:
    -   Person (7)
    -   Large vehicle (1)
-   Evaluate statistical differences
-   Investigate effect of range and azimuth

------------------------------------------------------------------------

### 3️⃣ Multiclass Model Training

-   Train multiclass classifier
-   Include interaction features where relevant
-   Resource-aware sampling for large dataset

Evaluation metrics:

-   AP (Average Precision) per class vs rest
-   mAP (mean Average Precision)
-   Training vs validation comparison

------------------------------------------------------------------------

### 4️⃣ Range & Azimuth Sensitivity Analysis

Evaluate whether:

-   AP improves at shorter ranges
-   AP improves near azimuth ≈ 0

------------------------------------------------------------------------

### 5️⃣ Precision-Oriented Operating Point Selection

-   Select PR curve threshold for "Person vs Rest"
-   Prioritize high precision
-   Evaluate Precision and Recall in validation using training threshold
-   Compare generalization behavior

------------------------------------------------------------------------

## 📈 Key Insights

-   Radar-based classification performance strongly depends on range and
    azimuth.
-   Certain classes (e.g., Person vs Large Vehicle) show distinguishable
    RCS behavior.
-   Precision-recall trade-offs are critical when prioritizing
    pedestrian detection safety.
-   mAP provides a robust overall performance measure across classes.

------------------------------------------------------------------------

## 🚀 How to Run

1.  Clone repository:

git clone
https://github.com/yourusername/radar-multiclass-object-classification.git

2.  Install dependencies

3.  Open notebook:

Entrega_2.ipynb

4.  Run all cells to reproduce training and evaluation

------------------------------------------------------------------------

## 🏭 Industrial Context

This project is framed within an industrial railway/autonomous detection
context and focuses on radar-based object classification under
real-world constraints.

------------------------------------------------------------------------

## 📚 Academic Context

Master's level coursework in Industrial & Intelligent Systems with focus
on applied Machine Learning and Perception Systems.

------------------------------------------------------------------------

## 📬 Author

Manuel de Prado García\
Master Data Analysis in Engineering\
Specialization in AI, Data Science & Data Anlysis