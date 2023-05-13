# **Predict whether income exceeds $50K/yr**

**Data Set Information:**

Extraction was done by Barry Becker from the 1994 Census database. A set of reasonably clean records was extracted using the following conditions: ((AAGE>16) && (AGI>100) && (AFNLWGT>1)&& (HRSWK>0))

** *Prediction task is to determine whether a person makes over 50K a year* **

**Attribute Information:**

Listing of attributes:

* earn: >50K, <=50K (**Target atribute**)

* age: continuous.
* workclass: Private, Self-emp-not-inc, Self-emp-inc, Federal-gov, Local-gov State-gov, Without-pay, Never-worked.
* fnlwgt: continuous.
* education: Bachelors, Some-college, 11th, HS-grad, Prof-school, Assoc-acdm, Assoc-voc, 9th, 7th-8th, 12th, Masters, 1st-4th, 10th, Doctorate, 5th-6th, Preschool.
* education-num: continuous.
* marital-status: Married-civ-spouse, Divorced, Never-married, Separated, Widowed, Married-spouse-absent, Married-AF-spouse.
* occupation: Tech-support, Craft-repair, Other-service, Sales, Exec-managerial, Prof-specialty, Handlers-cleaners, Machine-op-inspct, Adm-clerical, Farming-fishing, Transport-moving, Priv-house-serv, Protective-serv, Armed-Forces.
* relationship: Wife, Own-child, Husband, Not-in-family, Other-relative, Unmarried.
* race: White, Asian-Pac-Islander, Amer-Indian-Eskimo, Other, Black.
* sex: Female, Male.
* capital-gain: continuous.
* capital-loss: continuous.
* hours-per-week: continuous.
* native-country: United-States, Cambodia, England, Puerto-Rico, Canada, Germany, Outlying-US(Guam-USVI-etc), India, Japan, Greece, South, China, Cuba, Iran, Honduras, Philippines, Italy, Poland, Jamaica, Vietnam, Mexico, Portugal, Ireland, France, Dominican-Republic, Laos, Ecuador, Taiwan, Haiti, Columbia, Hungary, Guatemala, Nicaragua, Scotland, Thailand, Yugoslavia, El-Salvador, Trinadad&Tobago, Peru, Hong, Holand-Netherlands.


## Correlation Matrix:

![alt text](https://github.com/Cristhian-Ninanya/Predict_income_exceeds_50K/blob/master/images/correlation.png?raw=true)

* Apparently, some feature like 'fnlwgt', 'race' or 'native-country' have low correlation with target feature 'earn'.

## Results using Decision Tree

![alt text](https://github.com/Cristhian-Ninanya/Predict_income_exceeds_50K/blob/master/images/feature_import_tree.png?raw=true)

```
Train Accuracy: 75.81 %
Test Accuracy: 74.81 %
```
**OBS:**
* Using "Desicion Tree model", apparently features "marital-status" and "capital-gain" have more importace.
* Consider that accuracy for Train and test are too similar.
* Comparing "Feature Importances" and "Correlation" there are some feature like 'education' or 'sex' that should be compared.


## Results using Random Forest:

![alt text](https://github.com/Cristhian-Ninanya/Predict_income_exceeds_50K/blob/master/images/feature_import_forest.png?raw=true)

```
Accuracy_train:  99.05 %
Accuracy_test:  80.17 %
```

```
              precision    recall  f1-score   support

       <=50K       0.79      0.82      0.80      2322
        >50K       0.81      0.79      0.80      2383

    accuracy                           0.80      4705
   macro avg       0.80      0.80      0.80      4705
weighted avg       0.80      0.80      0.80      4705
```
## Confusion Matrix:

![alt text](https://github.com/Cristhian-Ninanya/Predict_income_exceeds_50K/blob/master/images/conf_matrix.png?raw=true)


**OBS:**
* "Accuracy_Test" improved using Random Forest, but "Accuracy_train" is almost overfitting. 
* Using random forest algorithm, feature like 'fnlwgt' and 'age' become more relevant than 'capital-gain'.
* 'education-num', 'relationship', 'hours-per-week' become more relevant than 'marital-stauts'.

**Final Observations:**

* "Random Forest provides higher precision compared to Decision Tree, but there are some factors to consider."
* "Random undersampling of the dataframe during training may influence the results."
* "The dataframe contains '?' values in multiple features."
* "When comparing the 'Correlation' and 'Random Forest Feature Importance' methods, there are many similarities, except for the feature 'fnlwgt' Further investigation is needed to understand the relevance of this feature."
