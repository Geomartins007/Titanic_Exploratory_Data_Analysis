# Titanic Exploratory Data Analysis: Exploring the survival rates.

## Table of Content
 - [Project Overview](#project-overview)
 - [Data Source](#data-source)
 - [Tools](#tools)
 - [Data Cleaning](#data-cleaning)
 - [Exploratory Data Analysis EDA](#exploratory-data-analysis-eda)
 - [Data analysis](#data-analysis)
 - [Results](#results)
 - [Limitation](#limitation)
 - [References](references)

### Project Overview

This data analysis project aims to provide insight into the survival rate of the passengers in the Titanic ship. By analysisng the relationships between different feature classes in the dataset, this analysis particularly hopes to throw insights on the survival rates per gender, passenger class, fare, siblings/partners/parents, and age. The analysis hopes to unveil the features categories of the individual feature classes that recieved attention during the rescue operation.

### Data Source

Titanic data: The primary datasets used for this analysis are the 'train_data.csv' and 'test_data.csv', containing the feature classes used in finding insights on the dataset. Both dataset were downloded for kaggle. [Click to download.](https://www.kaggle.com/code/mjamilmoughal/eda-of-titanic-dataset-with-python-analysis/input)

### Tools

- Pandas - Data cleaning, Exploratory Data Analysis (EDA)

- Seaborn - Data visualization

- Matplotlib - Data visualization

- MS PowerPoint - Report preparation

### Data Cleaning

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
ax= sns.countplot('Survived', 
              data= train_data)
plt.show()

#6 Visualize the survival by sex

sns.countplot('Survived', 
              hue= 'Sex',
              data= train_data)
plt.show()

#7 Visualize the survival by Passenger class

sns.countplot('Pclass', hue= 'Sex', data= train_data)

plt.show()

#8 Groupby to understand Survival vs SibSp

sib= train_data.groupby(['SibSp','Survived']).size().reset_index().rename(columns= {0:'Counts'})

#9 Passengers with the highest fare

train_data[train_data['Fare']==512.3292].style.background_gradient(cmap='summer_r')

#10 Saving plots and charts

plt.savefig("ax.png")

```
### Results

The EDA findings are summerized below;

1. The number of death cases are more than the survived cases in general.
2. 38.38% (342) and 61.62% (550) of the passsengers survived and died, respectively.
3. the 3rd class passengers suffered the most death.
4. It was observed that priority was given to 1st class passengers during the rescue operations.
5. regardless of class, the male are more than the female.
6. Most death and survival was between the age range of 16yrs and 51yrs.
7. The oldest rescued person was 80yrs old while the youngest survivor was less than a yeay old.
8. Passengers with that paid the highest Fare are in the 1st class category.
9. The barchart shows that the passengers with no siblings, parents or pathners had the highest survival.
    - as the number of siblings, parents or pathners decreases, the number of survival increses.
    - Therefore, there is an inverse relationship between the SibSp and Survived features.
    - A heatmap that shows a negative correlation value of -0.035 between the SibSp and the Survived features.

### Recommendation

Due to the nature of the dataset and the aim of the analysis, there no recommendation.

### Limitation

The age feature would have been better recorded as int and not the float dtype.

### References

1. Python Data Analysis with Pandas, NumPy, and Matplotlib by Fabio Nelli. [Download](https://indianpdf.com/python-data-analytics-pdf/)
2. MLJAR - [Saving Jupyter Notebook chart](https://mljar.com/blog/matplotlib-save-plot/#:~:text=For%20Jupyter%20Notebook%20users%2C%20you,file%20has%20an%20empty%20figure.)

