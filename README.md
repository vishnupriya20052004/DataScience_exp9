# Ex-09-Data-Visualization-

## AIM
To Perform Data Visualization on a complex dataset and save the data to a file. 

# Explanation
Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature generation and selection techniques to all the features of the data set
### STEP 4
Apply data visualization techniques to identify the patterns of the data.


# CODE AND OUTPUT
```
import seaborn as sns
import pandas as pd
import matplotlib.pyplot as plt
df=sns.load_dataset("tips")
print (df)
```
![image](https://github.com/Vaish-1011/ODD2023-Datascience-Ex-09/assets/135130074/3a4e3e8e-1a22-4fb5-817c-36a8146bf65c)

```
df.isnull().sum()
```
![image](https://github.com/Vaish-1011/ODD2023-Datascience-Ex-09/assets/135130074/b2eebf32-2d63-4370-a485-6759e7610ba0)

## FINDING OUTLIERS
```
plt.figure(figsize=(5,5))
plt.title("Data with outliers")
df.boxplot()
plt.show()
```
![image](https://github.com/Vaish-1011/ODD2023-Datascience-Ex-09/assets/135130074/5cc5f660-6ac3-4e83-96cd-ca6f3d2cd1ff)

## REMOVING OUTLIERS
```
plt.figure(figsize=(5,5))
cols=['total_bill','tip','size']
Q1=df[cols].quantile(0.25)
Q3=df[cols].quantile(0.75)
IQR=Q3-Q1
df=df[-((df[cols]<(Q1 - 1.5 * IQR))[df[cols]>(Q3 + 1.5 + IQR)]).any(axis=1)]
df.boxplot()
plt.show()
```
![image](https://github.com/Vaish-1011/ODD2023-Datascience-Ex-09/assets/135130074/193da607-9a70-4bef-bb6b-f696fdafa793)

## 1.Which day of the week has the highest total bill amount?
```
sns.barplot(x=df['day'],y=df['total_bill'],hue=df['day'])
plt.legend(loc="center")
plt.title("Highest Total Bill Amount of day of the week")
plt.show()
```
![image](https://github.com/Vaish-1011/ODD2023-Datascience-Ex-09/assets/135130074/ce3c53df-43ae-4ec9-a57b-c0cd3e3c9189)

## 2.What is the average tip amount given by smokers and non-smokers?
```
sns.boxplot(x=df['smoker'],y=df['tip'],hue=df['smoker'])
plt.title("Averaga tip amount given by somkers and non-smokers")
```
![image](https://github.com/Vaish-1011/ODD2023-Datascience-Ex-09/assets/135130074/fc31639f-ca10-4f74-8552-e6badd371316)

## 3.How does the tip percentage vary based on the size of the dining party?
```
df["tip_percent"]=df["tip"]/df["total_bill"]
sns.scatterplot(x=df['size'],y=df['tip_percent'],data=df)
plt.title("Tip percentage by dining party size")
```
![image](https://github.com/Vaish-1011/ODD2023-Datascience-Ex-09/assets/135130074/5a2e482e-5da0-4360-9d25-4ccd47ca19c1)

## 4.Which gender tends to leave higher tips?
```
sns.boxplot(x=df['sex'],y=df['tip'],hue=df['sex'])
plt.title("Tips based on gender")
```
![image](https://github.com/Vaish-1011/ODD2023-Datascience-Ex-09/assets/135130074/7a9793bb-4be1-4388-afd4-a75752e8d5b9)

## 5.Is there any relationshio between the bill amount and the day of the week?
```
sns.scatterplot(x=df['day'],y=df['total_bill'],hue=df['day'])
plt.legend(loc="best")
plt.title("Total bill amount by day of the week")
```
![image](https://github.com/Vaish-1011/ODD2023-Datascience-Ex-09/assets/135130074/afbb6fac-d7e6-4010-9280-56b643d2267d)

## 6.How does the distribution of total billa mounts vary across different time periods(lunch vs. dinner)?
```
sns.histplot(data=df,x="total_bill",hue="time",element="step",stat="density")
plt.title("Distribution of total bill amounts by time of day")
plt.show()
```
![image](https://github.com/Vaish-1011/ODD2023-Datascience-Ex-09/assets/135130074/651fc348-0270-4407-bc59-22f105931bb4)

## 7. Why dining party size group tends to have the highest average total bill amount?
```
sns.barplot(x=df['size'],y=df['total_bill'],hue=df['size'])
plt.title("Average total bill amount by dining party size")
plt.show()
```
![image](https://github.com/Vaish-1011/ODD2023-Datascience-Ex-09/assets/135130074/98c08200-45e9-463c-b32f-ec7454762e9f)

## 8.What is the distribution of tip amounts for each day of the week?
```
sns.boxplot(x="day",y="tip",data=df)
plt.title("Tip amount by day of week")
plt.show()
```
![image](https://github.com/Vaish-1011/ODD2023-Datascience-Ex-09/assets/135130074/1e00c719-c958-49d0-80f4-1d6917945374)

## 9.How does the tip amount vary based on the type of service (lunch vs. dinner)?
```
sns.violinplot(x="time",y="tip",data=df)
plt.title("Tip amount by time of day")
plt.show()
```
![image](https://github.com/Vaish-1011/ODD2023-Datascience-Ex-09/assets/135130074/3ee29aa2-5209-4154-b947-9ecc3d57be12)

## 10.Is there any correlation between the total bill amount?
```
sns.scatterplot(x="total_bill",y="tip",data=df)
plt.title("Correlation between tip amount and totalbill amount")
plt.show()
```
![image](https://github.com/Vaish-1011/ODD2023-Datascience-Ex-09/assets/135130074/63b5f866-8413-47eb-8f50-2a3dd7f611ce)

# RESULT
Thus the Data Visualization on a complex dataset is performed and saved the data to a file.
