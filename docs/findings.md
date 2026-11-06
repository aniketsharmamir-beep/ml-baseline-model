# Model Findings

## 1. Problem Statement
The goal is to predict whether a Titanic passenger survived (1) or did not survive (0), using details such as ticket class, sex, age, fare, and family size. Because the answer is a category, this is a classification problem.

## 2. Why Logistic Regression
Logistic Regression is the standard baseline model for yes/no outcomes. It is simple, fast to train, and easy to explain, which makes it a good starting point before trying more complex models.

## 3. Data Preparation
- Used the cleaned Titanic dataset (891 passengers) from a previous data cleaning task, with missing values already handled.
- Dropped PassengerId, Name, and Ticket because they are identifiers and carry no useful pattern.
- Converted the text columns Sex and Embarked into 0/1 columns, since machine learning models need numerical input.
- Separated the features (X) from the target (y = Survived).
- Split the data 80% for training and 20% for testing, using random_state=42 so the results can be reproduced.

## 4. Results
- Accuracy: 0.804
- F1-score: 0.755
- Confusion matrix (179 test passengers):
  - 90 correctly predicted as died
  - 54 correctly predicted as survived
  - 15 false alarms (predicted survived, actually died)
  - 20 missed survivors (predicted died, actually survived)

The plot is saved in images/evaluation_plots.png.

## 5. What the Results Mean
The model correctly predicted about 80% of the passengers in the test set (144 out of 179), which is a solid result for a first baseline model. The F1-score of 0.755 shows that it finds survivors reasonably well without raising too many false alarms.

The confusion matrix shows that the model makes more missed survivors (20) than false alarms (15). This means it is slightly more likely to predict that a passenger died when they actually survived.

The model is a useful starting point, but it can be improved. Next steps could include trying other models such as Decision Trees or Random Forest, creating new features from the data (for example family size), and testing with cross-validation for a more reliable score.
