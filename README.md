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

# Coding 
~~~
import pandas as pd
import numpy as np
import seaborn as sns
from scipy import stats

df=pd.read_csv("/content/SAMPLEIDS.csv")

print("INFO: ")
print(df.info())
print()

print("DESCRIBE: ",df.describe())
print()
print("After removing null values: ")
print(df.dropna())

data=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
df1=pd.DataFrame(data)
q1=df1.quantile(0.25)
q3=df1.quantile(0.75)
iqr=q3-q1
low=q1-1.5*iqr
high=q3+1.5*iqr
print()
print("LOWER BOUND: ",low)
print("HIGER BOUND: ",high)
print("IQR: ",iqr)
print("Q1: ",q1)
print("Q3: ",q3)

print()
df1=df1[((df1>=low)&(df1<=high))]
print("AFTER DROPPING OUTLIERS: ")
print(df1.dropna())
print()
print("CALCULATING Z SCORE: ")
print()
data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}
df2=pd.DataFrame(data)
z=np.abs(stats.zscore(df2))
print("Zscore: ",df2[z["weight"]>3])
~~~
# Output
![image](https://github.com/RakshithaK11/exno1/assets/139336455/89342d4b-7c83-4606-b3df-beb6146c5929)

![image](https://github.com/RakshithaK11/exno1/assets/139336455/5b34ce25-9920-42e8-a0d6-0e0d1d42fa9a)

![image](https://github.com/RakshithaK11/exno1/assets/139336455/76624442-026e-4a6b-a4ba-82213e5a33fc)

![image](https://github.com/RakshithaK11/exno1/assets/139336455/84cb4ae4-a7b9-411d-ac0f-fc8b3ea47e10)

# Result
thus, data cleaning process is done successfully.
