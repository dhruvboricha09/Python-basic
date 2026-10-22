
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# 1. Data Collecting and Loading
df = pd.read_csv("titanic.csv")

# 2. Data Understanding
print(df.head())
print(df.tail())
print(df.shape)
print(df.columns)
df.info()
print(df.describe())
print(df['Age'].describe())
print(df[df['Age'] == df['Age'].min()])
print(df['Fare'].describe())

# 3. EDA
print(df.dtypes)

# 3.1 Univariate Analysis
print(df['Sex'].unique())
print(df['Sex'].value_counts())
print(df['Survived'].unique())
print(df['Survived'].value_counts())
print(df['Pclass'].unique())
print(df['Pclass'].value_counts())
print(df['Embarked'].unique())
print(df['Embarked'].value_counts())
print(df['Fare'].describe())

df['Survived'].value_counts().plot(kind='bar')
plt.show()

df['Pclass'].value_counts().plot(kind='bar')
plt.show()

df['Age'].hist()
plt.show()

# 3.2 Bivariate Analysis
print(pd.crosstab(df['Sex'], df['Survived']))

pd.crosstab(df['Sex'], df['Survived']).plot(kind='bar')
plt.title('Survival by Sex')
plt.xlabel('Sex')
plt.ylabel('Number of Passengers')
plt.show()

print(pd.crosstab(df['Pclass'], df['Survived']))

pd.crosstab(df['Pclass'], df['Survived']).plot(kind='bar')
plt.title('Survival by Passenger Class')
plt.xlabel('Passenger Class')
plt.ylabel('Number of Passengers')
plt.show()

plt.scatter(df['Age'], df['Fare'])
plt.title('Age vs Fare')
plt.xlabel('Age')
plt.ylabel('Fare')
plt.show()

# 3.3 Multivariate Analysis
print(pd.crosstab(
    [df['Sex'], df['Pclass']],
    df['Survived']
))

plt.scatter(df['Age'], df['Fare'], c=df['Pclass'])
plt.title('Age, Fare and Passenger Class')
plt.xlabel('Age')
plt.ylabel('Fare')
plt.colorbar(label='Pclass')
plt.show()

# 4. Missing Value Analysis
print(df.isnull())
print(df.isnull().sum())

# 5. Data Preprocessing
df['Age'].fillna(df['Age'].mean(), inplace=True)
df['Embarked'].fillna(df['Embarked'].mode()[0], inplace=True)
df.drop('Cabin', axis=1, inplace=True)

print(df.isnull().sum())

# 6. Duplicate Data Check
print(df.duplicated().sum())

# 7. Feature Selection
df.drop(['PassengerId', 'Name', 'Ticket'], axis=1, inplace=True)

# 8. Correlation Analysis
numeric_df = df.select_dtypes(include='number')
print(numeric_df.corr())

corr_matrix = numeric_df.corr()
plt.imshow(corr_matrix)
plt.colorbar()
plt.xticks(range(len(corr_matrix.columns)), corr_matrix.columns, rotation=45)
plt.yticks(range(len(corr_matrix.columns)), corr_matrix.columns)
plt.show()

# 9. Outlier Detection
print(df[['Age', 'Fare']].head())
df.boxplot(column='Fare')
plt.show()

# 10. Final Dataset Check
df.info()
print(df.shape)

# 11. Save Cleaned Dataset
df.to_csv("cleaned_titanic.csv", index=False)
