# Supervised_Learning
## Instructions
this project use the imbalanced-learn library to resample the data and build and evaluate logistic regression classifiers using the resampled data. The datasets were inside of the challenge-resources file. This project include two parts: Sampling  and Ensemble Learners.
## Oversampling & Undersampling
## Oversampling
In this section, we will compare two oversampling algorithms to determine which algorithm results in the best performance. You will oversample the data using the naive random oversampling algorithm and the SMOTE algorithm. For each algorithm, be sure to complete the folliowing steps:

* View the count of the target classes using Counter from the collections library.
* Use the resampled data to train a logistic regression model.
* Calculate the balanced accuracy score from sklearn.metrics.
* Print the confusion matrix from sklearn.metrics.
* Generate a classication report using the imbalanced_classification_report from imbalanced-learn.

## Undersampling
In this section, you will test an undersampling algorithms to determine which algorithm results in the best performance compared to the oversampling algorithms above. You will undersample the data using the Cluster Centroids algorithm and complete the folliowing steps:

* View the count of the target classes using Counter from the collections library.
* Use the resampled data to train a logistic regression model.
* Calculate the balanced accuracy score from sklearn.metrics.
* Print the confusion matrix from sklearn.metrics.
* Generate a classication report using the imbalanced_classification_report from imbalanced-learn.

## Combination Sampling
In this section, you will test a combination over- and under-sampling algorithm to determine if the algorithm results in the best performance compared to the other sampling algorithms above. You will resample the data using the SMOTEENN algorithm and complete the folliowing steps:

* View the count of the target classes using Counter from the collections library.
* Use the resampled data to train a logistic regression model.
* Calculate the balanced accuracy score from sklearn.metrics.
* Print the confusion matrix from sklearn.metrics.
* Generate a classication report using the imbalanced_classification_report from imbalanced-learn.
## Ensemble Learners 
In this section, you will compare two ensemble algorithms to determine which algorithm results in the best performance. You will train a Balanced Random Forest Classifier and an Easy Ensemble AdaBoost classifier . For each algorithm, be sure to complete the folliowing steps:

* Train the model using the training data.
* Calculate the balanced accuracy score from sklearn.metrics.
* Print the confusion matrix from sklearn.metrics.
* Generate a classication report using the imbalanced_classification_report from imbalanced-learn.
* For the Balanced Random Forest Classifier onely, print the feature importance sorted in descending order (most important feature to least important) along with the feature score

# Findings
## Combination(Over and Undersampling results)
```python

                   pre       rec       spe        f1       geo       iba       sup

          0       0.01      0.70      0.74      0.03      0.72      0.52        87
          1       1.00      0.74      0.70      0.85      0.72      0.52     17118

avg / total       0.99      0.74      0.70      0.85      0.72      0.52     17205
```

## Precision (Sampling)

Compares between undersampling, oversampling and the combination. ALl the model perform bas in the precision. Since the low risk precision is approach to 100% and high risk has only 0.01. THe precision is the measure of the true positive prediction. This result can be due to the True negative has such a big sample.

## Recall 
Recall is the ability of the classifier to find all the positive samples. All three model has about ~75% of sensitivity . Overall, the best model that has the greatest recall value will be the combination of oversampling and undersampling

## F1 Score
The F1 Score does not really tell anything since the precision value for the high risk group is so low. this ccan cause the F1 score to be very low in th high score group. Since the denominator was so small. And for sure the F1 Score for low risk group will be very high. Overall, this result could not tell much things

## Ensemble Learner
```python

                   pre       rec       spe        f1       geo       iba       sup

          0       0.08      0.92      0.95      0.15      0.93      0.87        87
          1       1.00      0.95      0.92      0.97      0.93      0.87     17118

avg / total       0.99      0.95      0.92      0.97      0.93      0.87     17205
```

## Models’ performance
Performance: Random Forest Classifier -True Positive (Acutually =0 and Predict =0), the true positive is 59 -False Negative(Actually =0 and Predict =1), the false negative is 28 -False Positive(Acutally =1 and Predict =0), the false positive is 1821 -True Negative( Actually =1 and Predict =1), The true negative is 15297
## Precision
The precision refering to how many reliable a positive classification is. In the random forest classifier. the precision for high risk is 0.08 and 1 for low risk. From this result we can said this model predict a very poor high risk target. The low precision means large number of false positive. And the 100% precision for low risk means it succefully predict all the true positive for low risk target. In the AdaBoost classifier the precision result is pretty much close wihch is also not ideal

## Recall
Recall is the ability of the classifier to find all the positive samples. It can be determined by the ratio. Overall, both model perform a good recall value. A good recall value means there are large amount of true positive and less false negative.

## F1 Score
F1 Score is a weight average of true postive rate and precision, both model has low F1 score in high risk and high F1 Score for low risk.

The credit risk has two level low_risk and high _risk.In this notebook, we had implemented both Balanced Random Forest Classifier and Adaboost classifier. Based on the summary report we had, we can have some conclusion. Before talking about the result, we needs to clarify the number 0 means high risk and number 1 means low risk. in the random forest classifier, the precision of high risk is almost 0 and the low risk precision is 100%. Apparently, this classifer has an issue in indentifying the low-risk user. In turn of the sensitivity, the low-risk has achieve almost 70% and high risk ~90%, which means the model is really good at finding all the positive samples.The accuracy score for Random Forest classifier is 79% and 93% foe AdaBoost Classiifer. In turn of the accuracy score, the adaboost classifier perform a lot better. However, both model perform very bad in turn of precision. This mean it is very bad in positive classification. Therefore we cannot recommend both model. The major issue from this model is that the prediction of True Negative is too large. this can lead to calculation of precision and the Recall to be biased since the sample number was already been deviated so much.
