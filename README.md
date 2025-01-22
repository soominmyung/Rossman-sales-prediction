# Rossman Sales Prediction

## Project Overview

This project develops a sales prediction model for the Rossman drugstore chain. The dataset includes sales records, store-specific details, and other factors influencing sales. The goal is to predict sales for stores under different conditions using machine learning models, with a focus on regression trees and SHAP (Shapley Additive ExPlanations) for feature importance.

### Key Features:
- Extensive data preprocessing, including handling missing values and creating new variables.
- Feature engineering to improve model performance.
- Application of regression tree models for accurate sales predictions.
- Interpretation of results using SHAP values to analyze feature importance.

---

## Datasets

Three datasets were used in this study:
- **Store Dataset**: Contains information about 1,115 stores, including competition distance, assortment types, and promotion details.
- **Train Dataset**: Historical sales records from 01/01/2013 to 31/07/2015.
- **Test Dataset**: Similar structure to the Train dataset but lacks sales records, which need to be predicted.

---

## Data Preprocessing

### Issues Addressed:
1. **Missing Values**:
   - Missing values in `CompetitionDistance`, `CompetitionOpenSinceMonth`, and `CompetitionOpenSinceYear` were imputed using median or mean values.
   - Missing values in `Promo2SinceWeek`, `Promo2SinceYear`, and `PromoInterval` were handled by creating new variables.

2. **Categorical Variables**:
   - Variables such as `StoreType`, `Assortment`, and `DayOfWeek` were converted using one-hot encoding.

3. **Redundant Records**:
   - Rows with `Open=0` were removed as they provide no sales data.

4. **Customer Data**:
   - The `Customer` column was dropped since it was not a target for prediction.

---

## Feature Engineering

### New Variables Created:
1. **CompetitionDays**: Number of days a store has faced competition.
2. **Promo2Days**: Number of days a store participated in Promo2 up to the record date.
3. **Promo2Month**: Represents the time interval since Promo2 coupons were issued.

### Standardization:
All numerical variables were standardized to ensure consistent scale.

---

## Prediction Models

### Linear Regression Model:
- Used one-hot encoded data.
- **Performance**:
  - R²: 0.2194
  - RMSE: 0.8836
- Provided interpretable coefficients but lacked accuracy.

### Regression Tree Model:
- Captured complex relationships between variables.
- **Performance**:
  - R²: 0.9056
  - RMSE: 0.3072
- Chosen as the final model for predictions.

---

## Results and SHAP Analysis

### Feature Importance:
SHAP values provided insights into the contribution of each feature:
- **Top Factors:**
  - `Assortment_c`: Negative impact on sales.
  - `Promo`: Positive impact.
  - `CompetitionDistance`: Negative impact.
  - `DayOfWeek_5`: Lower sales on Fridays compared to Mondays.
- SHAP analysis revealed unexpected relationships, such as the limited impact of state holidays and the negative effect of prolonged competition.

---

## Limitations

1. **Model Exploration**:
   - Limited to regression trees and linear regression. Additional models (e.g., random forests, XGBoost) could improve performance.

2. **Feature Relationships**:
   - Further analysis is required to understand the interaction between features.

3. **Computational Resources**:
   - SHAP analysis was limited to the first 2,000 rows due to computation time.

---

## Conclusion

The regression tree model effectively predicts sales and provides valuable insights into key factors influencing sales. Feature engineering and SHAP analysis were critical for understanding variable importance. Future studies should explore additional models and hyperparameter tuning to enhance predictions.

---

## References

- Lundberg, S., & Lee, S. (2017). ‘A Unified Approach to Interpreting Model Predictions.’
- Steinberg, W. (2010). *Statistics Alive!*
- Additional references provided in the report.

For implementation details, refer to the codebase and documentation in the repository.
