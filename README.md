# CMAPSSDATA-CLassification
In this project, I proposed another type of solution to the problem CMAPSS. I make two types of classification to solve the prediction of RUL (Remaining Useful Life)


# Classification Project: Remaining Useful Life (RUL) Prediction

## Description
This project focuses on transforming a regression problem of predicting Remaining Useful Life (RUL) into a classification problem by defining categories based on RUL ranges. The approach simplifies the problem and allows for a detailed comparison of Naive Bayes and Logistic Regression classifiers across different data segments.

## Objectives
1. Simplify the regression problem into manageable classification categories.
2. Evaluate the performance of Naive Bayes and Logistic Regression models.
3. Analyze the effect of data segmentation using the `unit_class` feature on model performance.
4. Provide insights into which models perform best under different scenarios and requirements.

## Methodology
### Data Preprocessing
- **Feature Engineering**: Created new features, including `unit_class` to group data based on maximum cycle counts and `RUL_category` to classify instances by RUL.
- **Standardization**: Standardized sensor data using `StandardScaler`.
- **Feature Selection**: Removed features with low standard deviation.

### Models
1. **Naive Bayes**:
   - Implemented with dynamic smoothing.
   - Evaluated using Simple Cross-Validation (CV) and Stratified CV.
2. **Logistic Regression**:
   - Used Elastic Net regularization.
   - Evaluated with Simple CV and Stratified CV.

### Validation Metrics
- Accuracy
- Precision
- Recall
- F1 Score
- Execution Time

## Key Results

### General Model Performance
- **Naive Bayes**:
  - Fast execution (~2.78 seconds for both simple and stratified validation).
  - Moderate accuracy (~54.4% - 54.7%).
  - Lower precision and recall due to strong independence assumptions.
- **Logistic Regression**:
  - Slower execution (~45.6 seconds).
  - Higher accuracy (~70.8%) and robust metrics (Precision: ~62%, Recall: ~58.6%, F1 Score: ~57.5%).

### Performance by `unit_class`
- **Naive Bayes**:
  - Varies significantly across `unit_class` values.
  - Best performance at `unit_class = 5` (Accuracy: ~73%) but lower precision and F1 score (~50%).
  - Struggles with `unit_class = 0` (Accuracy: ~46%, F1 Score: ~43%).
- **Logistic Regression**:
  - Consistent performance across `unit_class` values (Accuracy: ~70%-81%).
  - Best results for `unit_class = 4` (Accuracy: ~81.5%).

## Conclusions
### General Insights
- Naive Bayes is faster and simpler but less precise and robust.
- Logistic Regression is slower but provides better overall performance, capturing dependencies between features effectively.

### Segment-Based Insights
- Data segmentation via `unit_class` highlights critical differences in model behavior.
- Logistic Regression adapts well to all groups, while Naive Bayes is preferable for scenarios requiring simplicity and speed.

### Recommendations
1. Use Logistic Regression for precision-critical applications.
2. Opt for Naive Bayes when computational resources are limited.
3. Consider hybrid strategies, applying different models based on `unit_class` to maximize performance.

## Author
**Carlos Alexis Barrios Bello**  
Master's Student in Artificial Intelligence, Universidad Veracruzana  
Email: zS23000636@estudiantes.uv.mx

## Acknowledgments
This project demonstrates the value of data segmentation and tailored model application in improving predictive performance for complex problems like RUL classification.
