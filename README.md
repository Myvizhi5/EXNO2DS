# EXNO2DS
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

## CODING AND OUTPUT
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.
```
import numpy as np
import seaborn as sns
import pandas as pd
import matplotlib.pyplot as plt
df=pd.read_csv("/content/titanic_dataset.csv")
df
```

<img width="1342" height="456" alt="image" src="https://github.com/user-attachments/assets/11b6fbb0-479e-4c83-a91f-4a79a8b77cc3" />

```
df.info()
```
<img width="457" height="392" alt="image" src="https://github.com/user-attachments/assets/0384a80d-32e8-43a3-9808-bc4d6b55d85d" />

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

```
df['PassengerId']=df['PassengerId'].fillna(df['PassengerId'].mean())
df['Survived']=df['Survived'].fillna(df['Survived'].median())
df['Pclass']=df['Pclass'].fillna(df['Pclass'].median())
df['Cabin']=df['Cabin'].fillna(df['Cabin'].mode()[0])
df
```
<img width="1360" height="592" alt="image" src="https://github.com/user-attachments/assets/3a16eff4-8da6-40e6-8ce3-e34494b40f95" />

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

```
num_cols = df.select_dtypes(include=['int64', 'float64']).columns
for col in num_cols:
    plt.figure(figsize=(5,3))
    plt.boxplot(df[col].dropna())
    plt.title(f"Boxplot of {col}")
    plt.xlabel(col)
    plt.show()
```

<img width="501" height="1071" alt="image" src="https://github.com/user-attachments/assets/39f2bcba-8820-442a-b4d0-40763e5c3287" />

```
plt=sns.boxplot(x='Pclass', y='Age', hue='Sex', data=df)
```

<img width="970" height="742" alt="image" src="https://github.com/user-attachments/assets/0bb88849-3323-441d-aec7-b9a0ebfde1c7" />

```
sns.scatterplot(x=df["Age"],y=df["Fare"])
```

<img width="645" height="512" alt="image" src="https://github.com/user-attachments/assets/d84da557-55b3-4657-be0c-07b6be017389" />

STEP 4: Remove the outliers using Inter Quantile Range method.

```
import pandas as pd
num_cols = df.select_dtypes(include=['int64', 'float64']).columns
for col in num_cols:
    Q1 = df[col].quantile(0.25)
    Q3 = df[col].quantile(0.75)
    IQR = Q3 - Q1  
    lower_bound = Q1 - 1.5 * IQR
    upper_bound = Q3 + 1.5 * IQR    
    df = df[(df[col] >= lower_bound) & (df[col] <= upper_bound)]
print(df)
```
<img width="767" height="797" alt="image" src="https://github.com/user-attachments/assets/5ae6b0e8-074b-4d6d-886f-a83e6d5f2955" />

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

```
sns.countplot(x='Sex', data=df)
plt.title("Countplot of Gender")
plt.show()
```
<img width="1026" height="817" alt="image" src="https://github.com/user-attachments/assets/02758802-5239-4de2-b4eb-405c6c3f383e" />

STEP 6: Use displot method to represent the univariate distribution of data.

```
df = pd.read_csv("titanic_dataset.csv")
sns.displot(df['Age'])
plt.title("Distribution of Age")
plt.show()
```
<img width="806" height="847" alt="image" src="https://github.com/user-attachments/assets/4ee33993-f2e9-43a4-a37c-80b615e2edcc" />

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

```
df = pd.read_csv("titanic_dataset.csv")
cross_tab = pd.crosstab(df['Sex'], df['Survived'])
print(cross_tab)
```
<img width="252" height="137" alt="image" src="https://github.com/user-attachments/assets/666a26db-5a4c-4dfa-b19a-2e881e370d97" />

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

```
df = pd.read_csv("titanic_dataset.csv")
corr = df.corr(numeric_only=True)
plt.figure(figsize=(8,6))
sns.heatmap(corr, annot=True)
plt.title("Heatmap of Correlation Matrix")
plt.show()
```
<img width="952" height="810" alt="image" src="https://github.com/user-attachments/assets/bcc4214c-d1e3-45cf-9f62-53cd7250fee3" />


# RESULT
Thus perform Exploratory Data Analysis on the given data set is implemented successfully.
