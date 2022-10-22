# Supervised Machine Learning Algorithms for Determining Credit Risk

Overview: A company LendingClub has provided credit card data in order to train supervised machine learning models. Several out-of-the box machine learning algorithms are available through imblearn and scikit that could be used to train the machine learning model. 6 models were compared and their performance evaluated to determine which model best serves this client.

Results:

RandomOverSampling
* Balanced Accuracy: 64.63% Fairly poor, not a great rate for credit risk analysis.
* Precision: Relatively high precision on the low risk, but terrible on the high risk.  A lot of false flagging for low risk as high risk
* Recall: Only caught 70% of high risk while false flagging 42% as high risk.

SMOTE
* Balanced Accuracy: 65.86% Fairly poor, not a great rate for credit risk analysis.
* Precision: Relatively high precision on the low risk, but terrible on the high risk.  A lot of false flagging for low risk as high risk
* Recall: Reduced true positive performance, of high risk, but also reduced false flagging of low risk 37%. 

ClusteredCentroids (UnderSampling)
* Balanced Accuracy: 54.42% Very poor, not a great rate for credit risk analysis.
* Precision: Relatively high precision on the low risk, but terrible on the high risk.  A lot of false flagging for low risk as high risk
* Recall: Gets around 70% of high risk flags correct, but drastically higher low risk false positives 60%.

SMOTEENN
* Balanced Accuracy: 63.61%
* Precision: Relatively high precision on the low risk, but terrible on the high risk.  A lot of false flagging for low risk as high risk
* Recall: Gets about 68% positively identified high risk but also false positive rate of 41% on low risk.  

BalancedRandomForestClassifier
* Balanced Accuracy: 79.26% Fair accuracy, model may need improvement.
* Precision: Good low risk precsion, but still only got about 3% on high risk.  Statistic is skewed because there are still 2013 false positives.
* Recall: High risk recall is roughly similar to previous models around 70% successful high risk true positive flags, but drastically reduced false positives of low credit risk individuals at only 12% false flagging.

EasyEnsembleClassifier (AdaBoost Model)
* Balanced Accuracy: By far the best model. 93.13% accuracy
* Precision: Low risk is fine.  3x improvement over random tree to high risk at 9%.  Data is again skewed because there were 994 false positive hits of high risk to actually low risk credit accounts.
* Recall: Very good high risk identification of 92%. Very good low risk identification.  only 6% of accounts were falsely flagged as high risk.

Summary:
The results of the data show that oversampling and undersample techniques were not very good at classification.  However ensemble methods using RandomTree and AdaBoost were much more successful at predicting low and high credit risk accounts.  The AdaBoost model is by far the best model.  However, in order to make a recommendation, the opportunity cost of 6% of accounts being false flagged for high credit risk, and 8% of accounts being false negatively flagged as low risk must be measured against manual review of accounts.  Theoretically paying someone to analyze tens of thousands of accounts could be more than the lost opportunity cost, however if the size of the account is very large, it could become a risk to the clients holdings.  The AdaBoost model is suggested but only against medium to low credit accounts.  Large credit accounts exceeding 1% of assets under management should probably be manually reviewed as incorrect flagging could have significant lost opportunity cost or cause exposure to high credit risk of defaults.
