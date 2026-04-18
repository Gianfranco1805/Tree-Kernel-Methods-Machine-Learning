## Project Overview
This project explores the application of unsupervised learning algorithms to identify behavioral patterns within a university student dataset. By analyzing features such as study habits, sleep patterns, and attendance rates, the project aims to discover hidden structures in student performance data without the use of pre-defined labels.

The analysis includes a from-scratch implementation of K-Means clustering, followed by a comparative study of Agglomerative Hierarchical Clustering and DBSCAN (Density-Based Spatial Clustering of Applications with Noise).

## Goals
* **Data Synthesis & Cleaning:** Preprocess raw student data by handling missing values, duplicates, and impossible outliers to ensure a high-quality dataset.
* **Algorithm Implementation:** Build a functional K-Means clustering algorithm using only NumPy and compare its efficiency against the industry-standard `scikit-learn` library.
* **Comparative Analysis:** Evaluate the strengths and weaknesses of different clustering paradigms (Centroid-based, Hierarchical, and Density-based).
* **Ground Truth Validation:** Quantify the effectiveness of unsupervised methods by measuring how well the discovered clusters align with actual student pass/fail outcomes.

## Tools & Technologies
| Category | Tools |
| :--- | :--- |
| **Language** | Python |
| **Data Manipulation** | Pandas, NumPy |
| **Machine Learning** | Scikit-learn (KMeans, DBSCAN, AgglomerativeClustering, StandardScaler) |
| **Statistical Analysis** | SciPy (Hierarchy Linkage & Dendrograms) |
| **Visualization** | Matplotlib, Seaborn |

## Methodology

### 1. Data Preprocessing
Raw data was cleaned using median imputation for missing values and Z-score normalization (StandardScaler). This step was critical to ensure that features with larger scales (like attendance rate) did not disproportionately influence distance-based calculations.

### 2. Implementation of Clustering Models
* **K-Means (Scratch + Sklearn):** Implemented the full iteration loop (Assignment and Update steps) to identify two distinct student profiles. The **Elbow Method** was utilized to determine that $K=2$ was the optimal cluster count.
* **Hierarchical Clustering:** Utilized **Ward’s Linkage** and visualized relationship structures through a **Dendrogram**. Compared Single, Complete, and Average linkages to observe the "chaining effect" versus cohesive grouping.
* **DBSCAN:** Investigated the dataset's density to isolate noise points (outliers). This was used to identify "contextual anomalies"—students whose behavior significantly diverged from the majority.

## Key Outcomes & Insights
* **Latent Structure Discovery:** Without any prior knowledge of pass/fail status, the K-Means model achieved an **85% alignment** with actual student outcomes. This proves that study habits and sleep are objective predictors of success.
* **The At-Risk Profile:** The model successfully isolated a cluster representing "At-Risk" students characterized by lower attendance and reduced sleep, providing a roadmap for early academic intervention.
* **Algorithm Efficiency:** Ward’s Hierarchical Clustering and K-Means provided the most balanced and actionable results, whereas DBSCAN’s density-based approach was highly sensitive to noise in this specific continuum of student data.

## Author
**Gianfranco Cisneros**
*Student at Florida International University (FIU)*
