# Titanic Exploratory Data Analysis: Exploring the survival rates.

### Project Overview

This data analysis project aims to provide insight into the survival rate of the passengers in the Titanic ship. By analysisng the relationships between different feature classes in the dataset, this analysis particularly hopes to throw insights on the survival rates per gender, passenger class, fare, siblings/partners/parents, and age. The analysis hopes to unveil the features categories of the individual feature classes that recieved attention during the rescue operation.

### Data Source

Titanic data: The primary datasets used for this analysis are the 'train_data.csv' and 'test_data.csv', containing the feature classes used in finding insights on the dataset. Both dataset were downloded for kaggle. [Click to download.](https://www.kaggle.com/code/mjamilmoughal/eda-of-titanic-dataset-with-python-analysis/input)

### Tools

- Pandas - Data cleaning, Exploratory Data Analysis (EDA)

- Seaborn - Data visualization

- Matplotlib - Data visualization

- MS PowerPoint - Report preparation

### Data Cleaning/Preparation

In the initial data preparion phase, the following tasks were carried out:

1. Loading dataset/inspections.
     - Info
     - Describe
2. Handling missing/null values.
   - Filling NaN with mode of the class.
   - Droping irrelevant classes.
   - Renaming classes.
  
### Exploratory Data Analysis (EDA)

Key questions to arrive at insights

1. Which passenger class has the higest death/survival rates?
2. Which Age has the higest death/survival rates?
3. Which Sex class has the higest death/survival rates?
4. What Sex recieved highest consideration during the rescue mission?
5. What Pclass recieved highest consideration during the rescue mission?
6. What Age recieved highest consideration during the rescue mission?
7. Were there passenger classes that recieved special attention during the rescue?
8. Who are the oldest/youngest survivor?
9. Who paid the highest fare?
10. How does having siblings, partner or parent affect survival?
11. Which passenger class has the higest death/survival rates?

### Data analysis

``` python

#1. Checking null values
train_data.isnull().sum()

#2. Filling null values
train_data['Age']= train_data['Age'].fillna(train_data['Age'].mode()[0])

#3. Dropping irrelevant columns
train_data= train_data.drop(columns= ['PassengerId', 'Ticket','Embarked', 'Cabin'])

#4. Correlations
sns.heatmap(train_data.corr(), annot= True)

#5. Some key visualisation codes
sns.countplot('Survived', 
              data= train_data)
plt.show()

```
