# Findings & Interpretation

## What the metrics mean for this problem

All three models achieve high overall accuracy (96–97%), which is meaningful because the class distribution is nearly balanced (~37% malignant, ~63% benign). However, **accuracy alone is not sufficient for cancer detection**. The more critical metric is **recall for the malignant class** — the fraction of actual cancers that the model correctly identifies.

A **false negative** (predicting benign when the tumour is actually malignant) means a missed cancer diagnosis, which can delay life-saving treatment. A **false positive** (predicting malignant when benign) leads to unnecessary follow-up procedures, but is far less dangerous.

| Model | Accuracy | Precision (M) | Recall (M) | F1 (M) |
|---|---|---|---|---|
| Logistic Regression | 96.49% | 0.975 | 0.929 | 0.951 |
| SVM (RBF) | 97.37% | **1.000** | 0.929 | 0.963 |
| Neural Network | 96.49% | 0.975 | 0.929 | 0.951 |

## How the models differ in their errors

All three models produce **identical recall (0.929)** for the malignant class on this test set, meaning each model misses the same number of actual malignant cases (false negatives). The key difference is in **precision**:

- The **SVM achieves perfect precision (1.000)** — every tumour it flags as malignant genuinely is malignant. There are zero false positives.
- **Logistic Regression and the Neural Network** both have precision 0.975 — they produce a small number of false alarms.

## Why the Neural Network does not outperform simpler models

The neural network (> 300 000 parameters) is heavily overparameterised for a 569-sample dataset. With full-batch training and 500 epochs, the training loss collapses to ~0.0000, a strong indicator of **overfitting** — the model memorises the training data rather than learning generalisable patterns. The result is test accuracy identical to Logistic Regression, with no benefit from the added complexity. Regularisation (dropout, weight decay) or a smaller architecture would be more appropriate for this dataset size.

## Limitations

1. **Small dataset:** 569 samples is insufficient to reliably train a deep neural network. Results should be interpreted with caution; performance estimates could shift meaningfully on a different split.
2. **Single train/test split:** A single 80/20 split gives one point estimate of performance. K-fold cross-validation would provide a more robust and statistically reliable estimate of generalisation error.
3. **Redundant features:** As shown in the feature correlation heatmap, `radius_mean`, `perimeter_mean`, and `area_mean` are almost perfectly correlated (|r| > 0.95). Retaining all three inflates model complexity without adding independent information. PCA or manual feature selection could reduce the feature space from 30 to ~15 without meaningful loss.
4. **Single dataset source:** The data comes from one institution (University of Wisconsin Hospitals). Model performance may not generalise to images captured with different equipment or clinical protocols.

## Ethics

- A model that predicts "benign" on a malignant tumour (false negative) can **delay diagnosis and treatment**, with potentially fatal consequences. Any clinical deployment must prioritise recall for the malignant class above all other metrics.
- This model must **not replace physician judgment**. It should be treated as a decision-support tool — one signal among many — reviewed by a qualified clinician before any diagnostic action is taken.
- The dataset was collected from a specific population and imaging protocol. **Demographic and equipment bias** has not been evaluated; performance for underrepresented populations is unknown.
- Any real-world clinical use would require **regulatory approval** (e.g., FDA clearance or Health Canada authorisation) and prospective clinical validation.
