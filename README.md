# Hadil Ghazal

## Dataset

The Kaggle Telco Customer Churn dataset, which contains 7,043 customer records (charges, account info, churn status) is used in this project to analyze which data elements are impactful in churn predictions and to compare interpretable models (Linear Regression, Logistic Regression, GAM).

## Assumption Checks

| Model | Key Assumptions Checked | Evidence | Concern |
|---|---|---|---|
| Linear regression | Linear relationships and behaviors | Residual Plot showed 2 distinct bands instead of random scatter | Binary Churn doesn't fit regression assumptions well |
| Logistic regression | Binary outcomes and relationships between continuous data elements and churn | Tenure showed a distinct trend, monthly and total charges showed nonlinear patterns | Linearity assumptions aren't satisfied in all cases |
| GAM | Nonlinear Relationships | CAM effect plots showed curved relationships in all three elements (tenure, monthly, total) | More complex than linear/logistic regression models |

## Model Comparison

| Model | Performance Evidence | Interpretability Strength | Interpretability Weakness |
|---|---|---|---|
| Linear regression |  MSE = 0.146, R2 = 0.252 | Easily Interpretable | Doesn't fit churn binary use case well |
| Logistic regression | Accuracy = 0.787, ROC AUC = 0.700 | Strong Interpretability for features that influence churn | Can miss relationships that are not linear |
| GAM | Accuracy = 0.797, ROC AUC = 0.704  | Shows more complex patterns in how customer features relate to churn | The curved effects take more effort to explain than a single coefficient |

## Recommendation

Recommended model: GAM

Why this model: 

GAM had the strongest performance of the three models with the highest accuracy and ROC AUC, and it also captured nonlinear patterns in the customer data that linear and logistic regression missed. That said, the outperformance over logistic regression was small so the added complexity should only be justified if that improvement translates into meaningful customer retention and long term revenue value


What the company can responsibly conclude:

Different customer characteristics are associated with various churn risks. While models can help identify customers who may be more likely to churn, it's important to stress test various data elements and best capture those features. While considering Monthly Charges can give one model approach an edge, it's possible that another feature like how often a customer uses the service could be another strong one. Before investing in an enterprise wide solution, it's important that the data and semantic layer is thoroughly combed through.


What the company should not conclude yet:

The company should not assume that these tested features cause churn. These models show relationships in the available data, but not proof that changing one of these features in isolation would prevent a customer from leaving. The company also shouldn't underestimate the data engineering step. Considerations should include outliers, combinations of features (like tenure + monthly charge + service utilization + customer support outreach frequency , and statistical research and sampling).


One next analysis we would run:

A natural next step would be to evaluate the financial value of the additional churn predictions made by GAM compared with logistic regression. For example, with a ~1% improvement, what would the long term revenue save look like, and how does that stack up against the cost of building either model? This would help determine whether the small performance improvement is actually worth the added complexity for the business.
