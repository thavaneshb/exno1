# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
```
import pandas as pd  
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
```
<img width="1204" height="834" alt="image" src="https://github.com/user-attachments/assets/364bc1ba-69d0-4b7f-a7ef-dbcf4c4b8218" />

```
df.head()
```

<img width="1200" height="265" alt="image" src="https://github.com/user-attachments/assets/717a5e99-f84a-47f5-9e5b-a4c7257bf2f1" />

```
df.tail()
```
<img width="1161" height="239" alt="image" src="https://github.com/user-attachments/assets/a14b7246-371d-4b78-a61c-6d3ec302bae8" />

```
df.info()
```

<img width="893" height="424" alt="image" src="https://github.com/user-attachments/assets/a3387d86-412c-4f77-a09d-6396881ead1a" />

```
df.describe()

```
<img width="1158" height="367" alt="image" src="https://github.com/user-attachments/assets/a04be8bc-af61-4259-ad15-f0a158104d3b" />

```
df.isnull().sum()
```

<img width="664" height="564" alt="image" src="https://github.com/user-attachments/assets/d1d57feb-3c31-455d-aff3-6052d8db7d93" />

```
df.isnull().any()

```
<img width="278" height="576" alt="image" src="https://github.com/user-attachments/assets/a6b425f6-e4c0-45be-91a0-053a42e27e4e" />

```
df.dropna()
```

<img width="1147" height="563" alt="image" src="https://github.com/user-attachments/assets/7c297388-0ffa-4c7b-ba20-edcefb22e1bc" />

```
df.fillna(0)
```

<img width="1127" height="743" alt="image" src="https://github.com/user-attachments/assets/97d2afb4-3ad4-4756-bbad-a68a47309168" />

```
df.fillna(method='ffill')
```

<img width="1441" height="745" alt="image" src="https://github.com/user-attachments/assets/f3d2dd36-ba16-4ca7-9b2c-ec3ca04df072" />

```
df.fillna({'GENDER':'MALE','NAME':'SRI'})
```
<img width="940" height="703" alt="image" src="https://github.com/user-attachments/assets/ff710fef-36dd-41b0-81d8-f3c214676442" />

```
ir=pd.read_csv("/content/iris (1).csv")
ir
```

<img width="727" height="425" alt="image" src="https://github.com/user-attachments/assets/20279f61-528a-43dc-8dc3-1f94bd3ad60a" />

```
ir.describe()
```

<img width="661" height="301" alt="image" src="https://github.com/user-attachments/assets/b53c7ae3-cfcb-43c1-bf0a-94d175bdc034" />

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```

<img width="691" height="466" alt="image" src="https://github.com/user-attachments/assets/ad961b32-d7bf-4102-b3e7-de20da1da583" />

```
Q1=ir.sepal_width.quantile(0.25)
Q3=ir.sepal_width.quantile(0.75)
(IQR)=Q3-Q1
print(IQR)
```
<img width="578" height="129" alt="image" src="https://github.com/user-attachments/assets/9e7f4cfa-c24e-4983-b239-f62dad5a0f09" />

```
ran=ir[((ir.sepal_width<(Q1-1.5*IQR))|(ir.sepal_width>(Q3+1.5*IQR)))]
ran['sepal_width']
```
<img width="296" height="203" alt="image" src="https://github.com/user-attachments/assets/15ef6b06-7656-4e44-ada5-33fc82e95d3a" />

```
ran=ir[~((ir.sepal_width<(Q1-1.5*IQR))|(ir.sepal_width>(Q3+1.5*IQR)))]
ran['sepal_width']

```
<img width="280" height="445" alt="image" src="https://github.com/user-attachments/assets/9a416c31-3a6b-472f-8e53-4997f24f3e41" />


```
sns.boxplot(x='sepal_width',data=ran)

```
<img width="609" height="465" alt="image" src="https://github.com/user-attachments/assets/a60c7f95-ad28-465a-8354-373ba23840e1" />

```
import numpy as np
import scipy.stats as stats
z=np.abs(stats.zscore(ir['petal_length']))
z
```
<img width="642" height="538" alt="image" src="https://github.com/user-attachments/assets/cd4aba5a-a4cc-4e13-984b-49537bc207b2" />

```
 ir1=ir[z<3]
ir1

```

<img width="614" height="424" alt="image" src="https://github.com/user-attachments/assets/7d25faaf-d00a-4f33-9c80-58813e32db10" />


# Result

 Thus the given data successfully performed data cleaning and saved the cleaned data to a file.
