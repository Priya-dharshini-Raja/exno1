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

# Coding:

Developed by: Priyadharshini Raja
Registration NUmber: 212223230160

## Data Cleaning: 
```
import pandas as pd
df=pd.read_csv("SAMPLEIDS.csv")
df
```
![image](https://github.com/user-attachments/assets/527f4534-b6b7-4e49-b05c-3a86db2aa587)
```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/5fa0661f-aeed-4bb5-a33a-68a7ae924620)
```
df.isnull().any()
```
![image](https://github.com/user-attachments/assets/a8a9e428-4f78-43d8-9868-7f0df0f5e952)
```
df.dropna()
```
![image](https://github.com/user-attachments/assets/e9245db6-a644-4422-be99-f0a33533bc2f)
```
df.fillna(0)
```
![image](https://github.com/user-attachments/assets/d46769cc-b6e3-40f1-96c9-3bbebb633644)
```
df.fillna(method = 'ffill')
```
![image](https://github.com/user-attachments/assets/5dc58f8d-beb1-40f1-8309-839d8d0c9190)
```
df.fillna(method = 'bfill')
```
![image](https://github.com/user-attachments/assets/db73a82a-5141-4ddf-bfa9-7281824c638a)
```
df_dropped = df.dropna()
df_dropped
```
![image](https://github.com/user-attachments/assets/60075e89-2637-4636-a3a0-b7863dd6a21e)
```
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![image](https://github.com/user-attachments/assets/32998fd0-83d8-4133-948f-8d571bf8b05a)


## IQR (Inter Quartile Range)

```
import pandas as pd
```
```
ir=pd.read_csv('iris.csv')
ir
```
![image](https://github.com/user-attachments/assets/e3072e03-f400-47e7-9107-13160b81f5eb)
```
ir.describe()
```
![image](https://github.com/user-attachments/assets/bfc972c4-e7dd-4dcb-a23c-46edfe14007e)
```
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/a30de128-ef36-4066-a475-1e84367c666d)
```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/user-attachments/assets/91cdd818-aa81-4f3e-b193-12a8aa1118a7)
```

rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/ebbe320d-c926-4b08-a8de-d214a26e7d33)
```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/user-attachments/assets/21583109-25f9-4d26-880f-e8546bb35b2d)
```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/851aea0b-a16a-4867-a676-5205b24e62f5)

## Z-Score:

```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
```
```
dataset=pd.read_csv("heights.csv")
dataset
```
![image](https://github.com/user-attachments/assets/ce85e16a-819c-4cbe-a8bd-f65a9c1d007b)
```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
```
```
iqr = q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/04da4fc5-c8ed-4304-bc86-e148a2fa234a)
```
low = q1 - 1.5*iqr
low
```
![image](https://github.com/user-attachments/assets/4b82f908-a361-4f44-a189-dae15398704a)
```
high = q3 + 1.5*iqr
high
```
![image](https://github.com/user-attachments/assets/3a16ea38-40c5-4b52-8db7-474baedfa3c7)
```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/user-attachments/assets/64e9c7f3-c3ab-4c97-85b7-067fe462dd75)
```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/user-attachments/assets/93a8f92a-c7be-418e-a89d-34a2348a0824)
```
df1 = df[z<3]
df1
```
![image](https://github.com/user-attachments/assets/d3d6a53a-4814-4e4f-b3f2-2ac19b36aa8d)

# Result

Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
