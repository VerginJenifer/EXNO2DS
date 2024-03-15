
# AIM:
To perform Exploratory Data Analysis on the given data set.
      
# EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODING AND OUTPUT:
```
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
from scipy import stats

df = pd.read_csv("/content/titanic_dataset (1).csv")


df.fillna(df.mean(), inplace=True)


plt.figure(figsize=(10, 6))
sns.boxplot(data=df.select_dtypes(include=np.number))  
plt.title('Boxplot of Numeric Data')
plt.show()


numeric_cols = df.select_dtypes(include=np.number).columns
for col in numeric_cols:
    q1 = df[col].quantile(0.25)
    q3 = df[col].quantile(0.75)
    iqr = q3 - q1
    low = q1 - 1.5 * iqr
    high = q3 + 1.5 * iqr
    df = df[((df[col] >= low) & (df[col] <= high))]

plt.figure(figsize=(8, 6))
sns.countplot(x='Sex', data=df)
plt.title('Countplot of Sex')
plt.show()

plt.figure(figsize=(8, 6))
sns.displot(df['Age'], kde=True)
plt.title('Distribution of Age')
plt.show()

cross_tab = pd.crosstab(df['Pclass'], df['Survived'])
print("Cross Tabulation:")
print(cross_tab)

plt.figure(figsize=(10, 8))
sns.heatmap(cross_tab, annot=True)
plt.title('Heatmap of Pclass vs Survived')
plt.show()
```
![image](https://github.com/VerginJenifer/EXNO2DS/assets/136251012/d3c7308f-2851-4448-a07d-2bc99310bb2f)
![image](https://github.com/VerginJenifer/EXNO2DS/assets/136251012/486b1291-690c-406c-81ab-929a56014411)
![image](https://github.com/VerginJenifer/EXNO2DS/assets/136251012/23d72318-9693-4ae5-973a-7e93df5dfa0f)
![image](https://github.com/VerginJenifer/EXNO2DS/assets/136251012/64cb65ab-5bce-4c53-b131-aa0a0639e97d)
![image](https://github.com/VerginJenifer/EXNO2DS/assets/136251012/886ba6e2-c379-46e5-973a-e0d9a84d2b90)



# RESULT:
Thus exploratory Data Analysis on the given data set is done successfully.
