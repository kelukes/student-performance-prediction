# student-performance-prediction
Exploratory data analysis and machine learning models to predict student success in an online learning platform. Classification and regression approaches using behavioral and demographic features.

## Overview

This project analyzes student performance data from an online course platform to identify patterns associated with academic success and build predictive models for early risk detection.

**Goal:** Predict student final scores (continuous and categorical) based on engagement metrics, demographics, and participation in support programs.

## Key Features

- **Comprehensive EDA:** Data quality assessment, missing value analysis, outlier detection, feature distributions
- **Feature Engineering:** Activity aggregations, engagement metrics, completion rates, log transformations
- **Classification Models:** Logistic Regression, PCA, Random Forest for 3-class prediction (low/mid/high performers)
- **Regression Models:** Linear Regression, Ridge with interaction terms for continuous score prediction
- **Model Comparison:** Cross-validation, hyperparameter tuning, interpretability analysis

## Results

### Classification Task (score groups: low/mid/high)
- **Best Model:** Logistic Regression with engineered features
- **Test Accuracy:** 0.92
- **Macro F1-Score:** 0.92
- **5-Fold CV F1:** 0.88 (stable across folds)

### Regression Task (continuous score 0-100)
- **Best Model:** Ridge Regression with feature engineering
- **Test R²:** 0.90
- **MAE:** 3.5 points
- **RMSE:** 5.2 points

### Key Predictors
1. **Mentoring participation** – strongest positive predictor
2. **Total platform activity** (logins, posts, lessons)
3. **Orientation course** participation
4. **Engagement intensity** (activity per hour)

Demographic features (age, country, gender) showed minimal predictive power.


## Methodology

### Data Preprocessing
- Handled inconsistent date formats and calculated snapshot years
- Normalized categorical variables (sex, country)
- Created binary flags for support program participation
- Imputed missing values using median/mode strategies

### Feature Engineering
- **Aggregated metrics:** `total_activity`, `total_learning`, `completion_rate`
- **Ratios:** `engagement_intensity`, `lessons_per_login`
- **Interactions:** `lessons × assignments`, `orientation × activity`
- **Transformations:** Log-scaled activity features for skewed distributions

### Models Evaluated
1. Baseline Logistic Regression (raw features)
2. Logistic Regression + feature engineering + L1 regularization
3. PCA + Logistic Regression (dimensionality reduction)
4. Random Forest (non-linear baseline)
5. Linear Regression (continuous score)
6. Ridge Regression + interactions (best regression model)

## Technologies Used

- **Python 3.11+**
- **ML & Stats:** scikit-learn, statsmodels
- **Data Processing:** pandas, numpy
- **Visualization:** matplotlib, seaborn
- **Statistical Tests:** scipy

## Business Insights

The analysis reveals that **structured support (mentoring, orientation) and consistent platform engagement are strongly linked to better outcomes**.

**Actionable recommendations:**
- Prioritize mentoring programs – highest impact on success
- Early identification of low-activity students for intervention
- Orientation course significantly enhances other activities' effectiveness
- Forum/discussion participation correlates with better performance

**Model limitations:**
- Models systematically underpredict very high scores (top 10% performers)
- Limited by current feature set – qualitative engagement data could improve predictions
- Small sample size for "high performer" class

## Note on Data

The dataset contains anonymized student records with engagement metrics and final scores. All personal identifiers have been removed. The notebook includes all outputs (visualizations, metrics, tables) to demonstrate methodology and findings.

## Key Findings

1. **Engagement matters more than demographics** – activity-based features explain 82% of score variance
2. **Mentoring has the largest effect** – ~19-point average score boost
3. **Non-linear patterns exist** – diminishing returns at very high activity levels
4. **Support programs work** – orientation enhances the effect of other activities

---

*Built as a capstone data science project demonstrating end-to-end ML workflow from EDA to model deployment recommendations for Tomorrow University* 


