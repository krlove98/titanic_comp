# Titanic - Machine Learning from Disaster
This repository contains a Jupyter notebook that tackles Kaggle’s famous Titanic problem. It uses a machine‑learning approach to predict which passengers survived the disaster based on different features. Below are descriptions of the dataset, the cleaning and pre‑processing techniques applied, and the models evaluated.

## Data
The original dataset from Kaggle includes information on 891 passengers of the Titanic. It contains 12 columns of different data types
raw.githubusercontent.com Some key variables are:

* PassengerId: passenger identification number.

* Survived: target variable indicating whether the passenger survived (1) or not (0).

* Pclass: ticket class (1st, 2nd or 3rd class).

* Name and Ticket: non‑numeric identification fields.

* Sex and Embarked: categorical variables describing gender and port of embarkation (C = Cherbourg, Q = Queenstown, S = Southampton) raw.githubusercontent.com
.

* Age, Fare, SibSp and Parch: numeric variables representing age, fare paid, number of siblings/spouses aboard and number of parents/children aboard, respectively.

Inspection of the data shows missing values in Age, Cabin and Embarked raw.githubusercontent.com.

## Cleaning and pre‑processing
Several operations were performed to prepare the data for modelling:

1. Imputation of missing values:

      * The Age variable had 177 missing values and was filled with the median age
raw.githubusercontent.com.

      * The Cabin column had more than 600 missing values; therefore, it was dropped from the dataset
raw.githubusercontent.com.

Missing values in Embarked were replaced with the mode (most frequent value)
raw.githubusercontent.com.

2. Encoding of categorical variables:

    * A one‑hot encoding was applied to the Sex variable, creating binary columns for male and female
raw.githubusercontent.com.

    * Embarked was encoded using LabelEncoder, assigning an integer to each port
raw.githubusercontent.com.

3. Removal of non‑useful features: The Name and Ticket columns were removed because they are free text not easily transformed into useful numeric variables raw.githubusercontent.com.

4. Data split: The data were separated into training and testing sets in an 80/20 ratio using train_test_split
raw.githubusercontent.com.

5. Feature scaling: A RobustScaler was used to reduce the influence of outliers, transforming the training and test sets to a comparable scale
raw.githubusercontent.com.

## Modelling
Several classification algorithms were explored to predict survival:

| Model                          | Brief description                                                 | Main metric                                                                                                                   |
| ------------------------------ | ----------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| **Logistic Regression**        | Binary linear model suitable for classification problems.         | Achieved an accuracy of **81 %** on the test set. The confusion matrix shows it predicts non‑survivors better than survivors. |
| **Decision Tree**              | Classifier based on decision rules.                               | Achieved an accuracy of about **75 %**.                                                                                       |
| **Random Forest**              | Ensemble of multiple decision trees that improves generalisation. | Was the most accurate model, with accuracy of around **82 %**.                                                                |
| **K‑NN (K Nearest Neighbors)** | Method based on voting among the nearest neighbours.              | Different values of *K* were tested to evaluate the error rate; it did not outperform logistic regression or random forest.   |


## Conclusions
* Careful data cleaning improved the quality of the training set: imputing Age, dropping Cabin and properly encoding categorical variables were essential steps.

* The random forest offered the best overall performance (~82 % accuracy)
raw.githubusercontent.com raw.githubusercontent.com, followed closely by logistic regression (~81 %)raw.githubusercontent.com. The simple decision tree performed notably worse, suggesting the ensemble of trees reduces overfitting.

* Although the K‑NN model was explored, it did not outperform the previous models and its performance was highly dependent on the choice of K
raw.githubusercontent.com.

## How to use this repository
1. Clone the repository:

git clone https://github.com/krlove98/titanic_comp.git

cd titanic_comp

2. Run the notebook:

* Open Titanic.ipynb in Jupyter Notebook or JupyterLab.

* Execute all cells sequentially to reproduce the data analysis, preparation and model training.

* The results, graphs and performance metrics will appear in the notebook.

## Credits
This project is an individual implementation of the “Titanic: Machine Learning from Disaster” challenge from Kaggle. The aim is to practise data preprocessing and supervised modelling techniques with scikit‑learn and compare several algorithms on a classic classification problem.
