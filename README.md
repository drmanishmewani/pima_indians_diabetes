This project represents a **comprehensive machine learning study** to identify the best algorithm for diabetes screening.
**10 different machine learning algorithms** from simple linear models to advanced ensemble methods were evaluated to find the optimal approach for early diabetes detection.

**Early detection is crucial** - to prevents diabetes complications like heart disease, kidney failure, and blindness.
Hence I focussed on getting 80% recall to catch at least 80% of diabetic patients (high sensitivity) while keeping false positives low.


# Process

1. **Exploration** of the PIMA Indian Diabetes Dataset
      - Class imbalance (65% non-diabetic, 35% diabetic)

2. **Data preprocessing**
      - Handled missing values (zeros treated as missing for biological features)
      - Removed one outlier value
      - Train-test split (80/20) with stratification
      - Standardized features using StandardScaler
      - Set random seed (42) for reproducibility
      - I used the transformed data for tree based and ensemble models too for the sake of maintaining similarity and simplicity of study across models


3. **Testing** 10 different machine learning algorithms:
      **Linear Models** (3):
      - Ridge Regression
      - Lasso Regression
      - ElasticNet

      **Non-Linear Models** (2):
      - K-Nearest Neighbors (KNN)
      - Support Vector Machine (SVM)

      **Probabilistic** (1):
      - Naive Bayes

      **Tree-Based** (1):
      - Decision Tree

      **Ensemble Models** (3):
      - Random Forest (Bagging)
      - AdaBoost (Discrete Boosting)
      - Gradient Boosting (Sequential Boosting)
      - XGBoost (Modern Gradient Boosting)

4. **Tuning hyperparameters** for each model

5. **Optimize decision thresholds** for clinical requirements (higher sensitivity)
      For clinical deployment:
      - Generated precision-recall curves
      - Found optimal thresholds for 80% recall target
      - Evaluated performance at custom thresholds

6. **Evaluate models** using multiple metrics
      **Primary Metric: Balanced Accuracy**
         - Handles class imbalance
         - Balances sensitivity and specificity
         - Clinically relevant
      **Supporting Metrics**:
         - Recall (Sensitivity) - patient safety
         - Precision (PPV) - resource efficiency
         - Specificity - correct non-diabetic identification
         - False Positives/Negatives - actual clinical impact
         - ROC AUC - discrimination ability
         - PR-AUC - performance on imbalanced data

      **Model Performance Summary**

      **Rank @ 80% Recall (Clinical Target):**
         
         1. Gradient Boosting: **75.7%** Balanced Accuracy
            - 30 False Positives (BEST)
            - 10 False Negatives
            - 59.5% Precision (BEST)
            - ROC AUC: 0.8224 (BEST)

         2. Random Forest & AdaBoost: 74.7%
            - 32 False Positives
            - Tied for 2nd place

         3. KNN: 74.2%
            - 33 False Positives
            - Strong non-parametric approach

7. **Final selection** of most appropriate model for deployment
      The study revealed that **Gradient Boosting** is the best model for diabetes screening as evident with the current dataset:

      **Balanced Accuracy: 75.7%** | Best overall performance |
      **Sensitivity (Recall): 81.5%** | Catches 44 out of 54 diabetics |
      **Specificity: 70%** | Correctly identifies 70% of non-diabetics |
      **Precision: 59.5%** | 6 out of 10 positive predictions are correct |
      **False Positives: 30**  | Fewest unnecessary follow-ups |
      **False Negatives: 10** | Misses 10 hard-to-detect cases |



# Insights:

1. Ensemble methods dominated the current study 
2. Class imbalance handling is crucial - Models without **class_weight='balanced'** performed worse
3. Hyperparameter tuning matters - Improved performance across models
4. Threshold optimization is essential to get the desired recall
5. sklearn Gradient Boosting > XGBoost (possibly due to smaller dataset)




**Balanced Performance**
- 70% specificity (avoids excessive false alarms)
- 59.5% precision (6 in 10 positive predictions correct)
- Only 10 missed cases (18.5% false negative rate)
