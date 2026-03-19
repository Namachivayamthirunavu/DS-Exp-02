# EXNO2DS
### AIM:
To perform Exploratory Data Analysis on the given data set.
      
### EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
### ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

### CODING AND OUTPUT
### Step 1: Import the Required Packages
```
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
```
### Step 2: Load the Dataset
```
# Replace 'your_data.csv' with your actual dataset filename
data = pd.read_csv('/content/titanic_dataset.csv')
```
### Step 3: Data Cleansing - Replace Null Values
```
# Step 3: Data Cleansing - Replace Null Values
# Use mean for numeric and mode for categorical values
for column in data.columns:
    if data[column].dtype == 'object':
        data[column] = data[column].fillna(data[column].mode()[0]) # Fill with mode
    else:
        data[column] = data[column].fillna(data[column].mean()) # Fill with mean
print(" Missing values handled.")
```
```
Output:
Missing values handled.
```
### Step 4: Boxplot to Analyze Outliers (e.g., Salary)
```
# Replace 'Salary' with a relevant numeric column from your dataset
sns.boxplot(x=data['Fare'])
plt.title("Boxplot - Fare")
plt.xlabel("Fare")
plt.show()
```
<img width="520" height="455" alt="image" src="https://github.com/user-attachments/assets/868a06c2-9769-4fc7-9916-098fda856451" />

### Step 5: Remove Outliers Using IQR Method
```
def remove_outliers_iqr(df, column):
 Q1 = df[column].quantile(0.25)
 Q3 = df[column].quantile(0.75)
 IQR = Q3 - Q1
 lower = Q1 - 1.5 * IQR
 upper = Q3 + 1.5 * IQR
 return df[(df[column] >= lower) & (df[column] <= upper)]
# Apply IQR method on 'Fare'
data = remove_outliers_iqr(data, 'Fare')
print("Outliers removed using IQR method.")
```
```
Output
Outliers removed using IQR method.
```
### Step 6: Countplot for Categorical Data
```
# Replace 'Department' with your own categorical column
sns.countplot(x='Embarked', data=data)
plt.title("Countplot - Embarked Distribution")
plt.xticks(rotation=45)
plt.show()
```
<img width="571" height="458" alt="image" src="https://github.com/user-attachments/assets/08740a40-c9bb-4f29-977d-669a89fd9665" />

### Step 7: Displot for Univariate Distribution (e.g., Age)
```
# Replace 'Age' with any numeric column
sns.displot(data['Age'], kde=True)
plt.title("Displot - Age Distribution")
plt.xlabel("Age")
plt.ylabel("Frequency")
plt.show()
```
<img width="489" height="512" alt="image" src="https://github.com/user-attachments/assets/2fe058a3-57c4-41c9-94da-62d67f0493d9" />

#### Step 8: Cross Tabulation to Analyze Relationships
```
# Example: Gender vs Department
crosstab_result = pd.crosstab(data['Sex'], data['Embarked'])
print("\nCross Tabulation Result:")
print(crosstab_result)
```
```
Output
Cross Tabulation Result:
Embarked   C   Q    S
Sex                  
female    40  35  169
male      76  40  415
```
### Step 9: Heatmap to Show Relationships (Correlation Between Variables)
```
# Only numeric columns are considered for correlation
correlation_matrix = data.corr(numeric_only=True)
sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm')
plt.title("Correlation Heatmap")
plt.show()
```
<img width="596" height="505" alt="image" src="https://github.com/user-attachments/assets/2751d47b-215d-4273-888f-7d3d6228e9fb" />

# RESULT
Thus the program to implement the data analysis has been successfully completed
