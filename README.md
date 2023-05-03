# Giskard_tech_case

## Summary

### Data Augmentations performed :

1. Feature Engineering :

1.1 Categorical Encoding changed from Onehot to Target-encoding (WOE encoding)

1.2 Numerical Feature binning, Scaling and creation

1.3 Interaction Variables Creation

2. Imbalanced data handling:

2.1 Synthetic random sampling using SMOTE, SmoteTOMEK

3. Feature Selection and Regularization :

3.1 Lasso and Ridge trials with base logistic model

3.2 Feature selection trials based on top K features (F-clasif, chi-squared) and logits p-value significance

### Conclusion and Observations:

* As we are performing an imbalanced classification task of credit scoring, Accuracy would not be a good metric to observe. Also, business would bleed more if we wrongly predict defaults as non-defaults; vis-a-vis non-defaults as defaults (Recall of defaults vs Recall of non-defaults), a focus on precision-recall tradeoff for defaults, F1-score and auc-roc should be kept over accuracy.

* Various combinations of the above augmentations were tried, and best performance across the selected classification metrics was observed in the setup with Weight-of-evidence encoding (WOE) + all base features + SMOTEtomek sampling was achieved.

* For around 3% loss in overall test-accuracy, we were able to achieve 32% increase in Recall for default-class with 6% drop in precision, achieve 10% increase in Precision for non-default class with 15% drop in Recall. Overall a 2% increase in overall macro-F1 score and 0.5 basis-points increase in Auc-roc metric

## Assigned Task

In this exercise, we ask you to improve the performance of this model using data augmentation.

To do that, we’ll ask you to

Generate some new data examples
Retrain the same logistic regression model with the new data examples
Compute the performance metrics of your new model. It should be higher than the initial model trained with the non-augmented data
You can propose any data augmentation strategy, but

We ask you to propose at least two data augmentation techniques

Focus your data augmentation strategy on data slices that underperform. For instance, the following data slices have low performances:

credit_history == ”all credits at this bank paid back duly”
purpose== ”Other”
duration_in_month==36
account_check_status == "<0 DM”
Don’t overfit your validation dataset. We strongly value augmentation strategies that come from domain knowledge/heuristics instead of brute force

Hints: To get some domain intuition on the behavior of your model, you can use the AI Inspector of Giskard. See the installation and the upload process in the doc. This is not a mandatory requirement!
