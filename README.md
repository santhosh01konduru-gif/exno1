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
~~~
Name:KONDURU SANTHOSH
Registration:212225240074
~~~
~~~
import pandas as pd
data=pd.read_csv("SAMPLEIDS.csv")
data
~~~
<img width="1014" height="786" alt="image" src="https://github.com/user-attachments/assets/c1ba6d06-9be3-485b-a95e-b697f7f29985" />
~~~
data.head()
~~~
<img width="981" height="246" alt="image" src="https://github.com/user-attachments/assets/a113bdc2-b55c-4973-8be7-e2babdd4807a" />
~~~
data.tail()
~~~
<img width="831" height="192" alt="image" src="https://github.com/user-attachments/assets/9a6af8cc-1b8b-4f25-9cc0-8f930ebdf531" />
~~~
data.isnull()
~~~
<img width="711" height="647" alt="image" src="https://github.com/user-attachments/assets/33bca6a5-faed-4ae7-a910-7d473747ff1b" />
~~~
data.isnull().sum()
~~~
<img width="136" height="269" alt="image" src="https://github.com/user-attachments/assets/323076ea-70db-4b0d-a314-9675005b198f" />
~~~
data.isnull().any()
~~~
<img width="156" height="274" alt="image" src="https://github.com/user-attachments/assets/366fd1c1-7e09-46c0-849c-c9570d3d88b0" />
~~~
data.dropna()
~~~
<img width="792" height="392" alt="image" src="https://github.com/user-attachments/assets/680eb6bf-cfb8-4867-a863-a5a0b46ebcb9" />
~~~
data.fillna(0)
~~~
<img width="798" height="609" alt="image" src="https://github.com/user-attachments/assets/84b0bc9c-88ac-440c-a31f-d78f1a7862bb" />
~~~
data.fillna(method='ffill')
~~~
<img width="800" height="630" alt="image" src="https://github.com/user-attachments/assets/392f3c5b-82ce-4c2b-9423-e42b5f166e3e" />
~~~
data.fillna(method='bfill')
~~~
<img width="803" height="609" alt="image" src="https://github.com/user-attachments/assets/4eba55db-e0ec-4af1-96f5-73fc1c0be214" />
~~~
data.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
~~~
<img width="801" height="608" alt="image" src="https://github.com/user-attachments/assets/d294273b-3751-493a-bea5-57010cf4c5c5" />
~~~
IQR(Inter Quartile Range)
import pandas as pd
ir=pd.read_csv("iris.csv")
ir
~~~
<img width="517" height="388" alt="image" src="https://github.com/user-attachments/assets/3ab06a17-d053-4008-8d83-07531403fda3" />
~~~
ir.describe()
~~~
<img width="442" height="279" alt="image" src="https://github.com/user-attachments/assets/ae193879-c6a8-4221-b2eb-74ba160a9ac5" />
~~~
ir.shape
~~~
<img width="105" height="49" alt="image" src="https://github.com/user-attachments/assets/9f6d69d3-7574-441b-9024-f0717d741bd9" />
~~~
ir.info()
~~~
<img width="385" height="241" alt="image" src="https://github.com/user-attachments/assets/e0ab0411-ccce-4748-a2c7-14d3114ba9b0" />
~~~
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
<img width="615" height="530" alt="image" src="https://github.com/user-attachments/assets/d55f1257-c922-47be-a6b1-1288c859ef71" />
 q1=ir.sepal_width.quantile(0.25)
 q3=ir.sepal_width.quantile(0.75)
 iqr=q3-q1
 print(iqr)
~~~
 <img width="105" height="33" alt="image" src="https://github.com/user-attachments/assets/528c94c4-7356-464d-b596-04f0315e1bd9" />
 ~~~
 out=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
 out['sepal_width']
~~~
<img width="355" height="104" alt="image" src="https://github.com/user-attachments/assets/6fdf1849-0379-4520-8026-9471147fd25d" />
 ~~~
 nor=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
 nor['sepal_width']
~~~
<img width="472" height="253" alt="image" src="https://github.com/user-attachments/assets/f7a59e25-722b-4712-b6c8-e2e88abe47f7" />
~~~
sns.boxplot(x='sepal_width',data=nor)
~~~
<img width="658" height="538" alt="image" src="https://github.com/user-attachments/assets/f84bfe0e-e584-4f82-8db8-efa154cc6543" />

Z-SCORE
~~~
import numpy as np
import pandas as pd
df=pd.read_csv("heights.csv")
df
~~~
<img width="216" height="441" alt="image" src="https://github.com/user-attachments/assets/64703695-bb84-4745-85a0-26c3b0d0f6c2" />
~~~
import scipy.stats as stats
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
iqr = q3-q1
iqr
~~~
<img width="207" height="48" alt="image" src="https://github.com/user-attachments/assets/c673bb5e-f7ae-440d-a84d-7fbb7b74446f" />
~~~
low = q1 - 1.5*iqr
print(low)
high = q3 + 1.5*iqr
print(high)
~~~
<img width="173" height="49" alt="image" src="https://github.com/user-attachments/assets/51e9dfe1-6509-4c3a-bc95-1035e89f04b1" />
~~~
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
~~~
<img width="167" height="376" alt="image" src="https://github.com/user-attachments/assets/e00158e6-3688-464f-8b7c-cbd170d20016" />
~~~
z = np.abs(stats.zscore(df['height']))
z
~~~
<img width="331" height="300" alt="image" src="https://github.com/user-attachments/assets/8f5a40ca-a143-4042-bf84-b62965fdd13c" />

~~~
df1 = df[z<3]
df1
~~~
<img width="228" height="412" alt="image" src="https://github.com/user-attachments/assets/4dd168a6-04ac-41bb-ae73-f6cd11913be4" />


# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
