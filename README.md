# Housing_dataset-Analysis



## Dataset

In this project, I used Credit Card Data from book "Econometric Analysis" and the California Housing Prices data from Kaggle.

Here's a wget-able [link](https://raw.githubusercontent.com/alexeygrigorev/datasets/master/AER_credit_card_data.csv):

wget https://raw.githubusercontent.com/alexeygrigorev/datasets/master/housing.csv

```bash
wget https://raw.githubusercontent.com/alexeygrigorev/datasets/master/AER_credit_card_data.csv
```
The goal of this project is to inspect the output of different evaluation metrics by creating a classification model (target column `card`). 


## Preparation

* Create the target variable by mapping `yes` to 1 and `no` to 0. 
* Split the dataset into 3 parts: train/validation/test with 60%/20%/20% distribution. Use `train_test_split` function for that with `random_state=1`.


## Evaluation metric

ROC AUC could also be used to evaluate feature importance of numerical variables. 

* For each numerical variable, computed AUC with the `card` variable.
* Use the training dataset was used for that

## Training the model

From now on, I used these columns only:

```
["reports", "age", "income", "share", "expenditure", "dependents", "months", "majorcards", "active", "owner", "selfemp"]
```

Apply one-hot-encoding using `DictVectorizer` and train the logistic regression with these parameters:

```
LogisticRegression(solver='liblinear', C=1.0, max_iter=1000)
```


Precision and recall are conflicting - when one grows, the other goes down. That's why they are often combined into the F1 score - a metrics that takes into account both

This is the formula for computing $F_1$:

$$F_1 = 2 \cdot \cfrac{P \cdot R}{P + R}$$

Where $P$ is precision and $R$ is recall.


Use the `KFold` class from Scikit-Learn to evaluate our model on 5 different folds:

```
KFold(n_splits=5, shuffle=True, random_state=1)
```
## Author

Joseph Ariyo
