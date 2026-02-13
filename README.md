# Student-Performance-Analysis

# Author: Prithujit Ghosh

Project Goal: To identify at-risk students before final exams using behavioral, demographic, and interim academic data.

**📊 Project Overview:**
This project focuses on building a robust data pipeline to predict student grades. The core philosophy is Early Intervention: predicting outcomes using only the data available during the semester (Midterms, Quizzes, Attendance) and excluding "leaky" post-semester data like Final Scores.

**🛠 Notebook Structure & Methodology**
1. Data Cleaning & Preprocessing
Initial Analysis: Basic sanity checks on numerical ranges and logical bounds.

Data Quality Assessment: Identifying missing values and handling redundant features (e.g., dropping Total_Score to prevent data leakage).

2. Advanced Imputation Strategy
Categorical Imputation: Instead of simple mode-filling, a Random Forest Classifier was used to impute Parent_Education_Level. This preserves the original category distribution and avoids fractional "mean" values.

Success Assessment: Validated the imputation by comparing "Before vs. After" distribution percentages to ensure no statistical bias was introduced.

3. Feature Engineering & Transformation
New Feature Creation:

Academic Efficiency: (Midterm Score / Study Hours) to identify high-effort vs. low-effort learners.

Burnout Index: (Stress Level / Sleep Hours) to capture the physiological impact on performance.

Inconsistency Score: Standard deviation across all scores to find "unpredictable" at-risk students.

Feature Transformation: Applied Log Transformation and IQR-based Winsorization (Clipping) on right-skewed features like Academic_Efficiency to normalize distributions for correlation analysis.

4. Statistical Validation
Correlation Analysis: Used heatmaps to identify prdictors.

Multicollinearity (VIF): Calculated Variance Inflation Factors to ensure engineered features provided unique signals. All final features were maintained below a VIF of 5.0.
