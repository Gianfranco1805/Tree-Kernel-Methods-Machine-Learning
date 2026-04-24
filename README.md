## Project Overview
This project explores the limitations of linear models when applied to datasets with complex, nonlinear relationships. Specifically, it predicts student exam outcomes (Pass/Fail) based on behavioral features (`hours_studied`, `sleep_hours`, `attendance_rate`, `prev_exam_score`). 

The core challenge of this dataset is the **"burnout effect"**—a nonlinear pattern where excessive studying negatively impacts performance. To capture this, the project implements and compares traditional linear models against advanced tree-based and kernel-based algorithms.

## Technologies Used
* **Python 3.11+**
* **NumPy** & **Pandas** (Data manipulation and custom algorithm implementation)
* **Scikit-Learn** (Model training, evaluation, and hyperparameter tuning)
* **Matplotlib** & **Seaborn** (Data visualization and decision boundary plotting)

## Key Features & Implementation
### 1. Data Preprocessing & EDA
* Handled missing data via median imputation and removed statistical outliers/impossible values.
* Applied strict Z-score normalization, computing parameters exclusively from the training set to ensure **no data leakage**.
* Conducted Exploratory Data Analysis (EDA) and generated a correlation matrix to expose the nonlinear correlation of `hours_studied`.

### 2. From-Scratch Decision Tree (NumPy)
* Implemented a custom Decision Tree classifier natively in NumPy using CART algorithm principles.
* Programmed custom functions for calculating **Gini Impurity** and **Information Gain**.
* Constructed a recursive tree-building algorithm with explicit stopping conditions (`max_depth`, `min_samples_split`).
* Validated the custom implementation's accuracy and root-split logic against `sklearn.tree.DecisionTreeClassifier`.

### 3. Overfitting & Bias-Variance Analysis
* Trained decision trees across multiple depths to evaluate the **Bias-Variance Trade-off**.
* Plotted depth vs. accuracy curves (Training vs. Cross-Validation) to visually identify the exact threshold where the model transitioned from underfitting (high bias) to overfitting (high variance).

### 4. Support Vector Machines (SVM) & The Kernel Trick
* Compared Linear, Polynomial (degree 2), and Radial Basis Function (RBF) kernels.
* Visualized 2D decision boundaries to demonstrate how the **Kernel Trick** allows the RBF kernel to mathematically map data into higher dimensions, successfully isolating the "burnout" cluster.
* Utilized `GridSearchCV` to optimally tune the `C` (margin strictness/regularization) and `gamma` hyperparameters through 5-fold cross-validation.

### 5. Random Forest & Ensemble Learning
* Trained an ensemble of 100+ decision trees to combat individual tree variance via **Bagging** (Bootstrap Aggregating) and feature randomization.
* Evaluated model generalization using Out-Of-Bag (OOB) accuracy.
* Extracted and visualized Gini feature importances, noting the differences between nonlinear pattern recognition and linear correlation.

## Key Findings
* **The Failure of Linear Models:** Logistic Regression and Linear SVM struggled significantly as they attempted to draw a monotonic boundary through a clearly non-monotonic dataset. They failed to recognize that studying 15 hours yielded worse results than studying 6 hours.
* **The Power of RBF:** The tuned RBF SVM achieved highly competitive test accuracy by drawing an enclosed boundary around the "optimal study zone."
* **Ensemble Stability:** The Random Forest proved that increasing `n_estimators` effectively lowered model variance without causing overfitting, cementing it as a highly robust classifier.
* **Accuracy vs. Interpretability:** While the ensemble and kernel methods yielded the highest accuracy, the single Decision Tree remained the most interpretable model for generating human-readable "if-then" rules.
