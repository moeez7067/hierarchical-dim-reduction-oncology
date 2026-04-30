# hierarchical-dim-reduction-oncology
A machine learning deep-dive into oncology 🔬 I built a progressive dimensionality reduction pipeline (PCA to t-SNE) to classify RNA-Seq tumor samples with 99.38% accuracy. Explores manifold learning in bioinformatics.
# High-Performance Cancer Classification using RNA-Seq Data 🧬📉

## Overview
This project implements a comprehensive machine learning pipeline to classify five distinct cancer types (BRCA, COAD, KIRC, LUAD, and PRAD) using high-dimensional genomic data. By addressing the "curse of dimensionality" inherent in RNA-Seq datasets, the project demonstrates a hierarchical progression of dimensionality reduction techniques, culminating in a highly accurate classification model.

## Dataset
The data is sourced from the **UCI Gene Expression Cancer RNA-Seq dataset**. It comprises 801 tumor samples, each containing 20,531 gene expression features. 
*   *Note: Due to file size limits, the raw dataset is not hosted in this repository. It can be accessed directly from the [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/401/gene+expression+cancer+rna+seq).*

## Methodology & Pipeline
The project workflow is divided into three core phases:

### 1. Preprocessing & Biomarker Discovery
*   Applied a **Variance Threshold filter** to remove constant, zero-variance genes.
*   Utilized the **Chi-Squared statistical test** (`SelectKBest`) to isolate the top 20 most significant biomarkers indicative of specific cancer types.
*   Standardized the data using `StandardScaler` to ensure optimal manifold learning and SVM performance.

### 2. Hierarchical Dimensionality Reduction
A progressive approach was used to compress the 20,000+ features while preserving critical biological variance:
*   **Baseline (Linear):** Principal Component Analysis (PCA) retaining 95% of the variance.
*   **Advanced (Non-Linear):** t-Distributed Stochastic Neighbor Embedding (t-SNE) applied to the PCA projections to capture complex manifold structures and resolve overlapping clusters. 
*(See the PCA vs. t-SNE projection plot in the `images` folder for visual comparison).*

### 3. Classification & Evaluation
To prevent data leakage, an 80/20 stratified train-test split was implemented prior to feature selection and scaling. The transformed data was evaluated across multiple algorithms:
*   **Support Vector Machine (SVM):** Linear kernel, C=1.0. 
*   **k-Nearest Neighbors (k-NN):** n_neighbors=5.
*   **Random Forest Classifier:** n_estimators=100.

## Key Results
The combination of targeted biomarker discovery, t-SNE dimensionality reduction, and SVM classification yielded state-of-the-art results:
*   🏆 **SVM Accuracy:** 99.38% (F1-Score: 1.00 for COAD, KIRC, PRAD)
*   **k-NN Accuracy:** 97.52%
*   **Random Forest Accuracy:** 89.44%

## Repository Structure
*   `final_project_machine_learning2.ipynb`: The core Jupyter Notebook containing the end-to-end code.
*   `Project_Proposal.pdf`: Detailed methodology and biological rationale.

## How to Run
1. Clone this repository: `git clone https://github.com/[Your-Username]/cancer-classification-rna-seq.git`
2. Download the `data.csv` and `labels.csv` from the UCI repository and place them in the appropriate drive/local directory.
3. Update the file paths in the Jupyter Notebook to match your local setup.
4. Run the notebook sequentially.

## Author
**Abdul Moeez**
*   [LinkedIn Profile](https://www.linkedin.com/in/abdul-moeez-aa8593378/)
