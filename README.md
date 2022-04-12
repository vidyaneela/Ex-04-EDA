# Ex-04-EDA
## AIM
To perform EDA on the given data set.

## Explanation
The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.

## ALGORITHM
## STEP 1 :
Import the required packages(pandas,numpy,seaborn).

## STEP 2 :
Read and Load the Dataset

## STEP 3 :
Remove the null values from the data and remove the outliers.

## STEP 4 :
Remove the non numerical data columns using drop() method.

## STEP 5:
returns object containing counts of unique values using (value_counts()).

## STEP 6:
Plot the counts in the form of Histogram or Bar Graph.

## STEP 7:
find the pairwise correlation of all columns in the dataframe(.corr()).

## STEP 8:
Save the final data set into the file.

## CODE:
```
import pandas as pd 
import seaborn as sns
import matplotlib.pyplot as plt
df= pd.read_csv('supermarket.csv')
df.head()
df.info()
df.isnull().sum()
df.boxplot()
cols = ['Tax 5%', 'Total','gross margin percentage','Payment']
Q1 = df[cols].quantile(0.25)
Q3 = df[cols].quantile(0.75)
IQR = Q3 - Q1
df = df[~((df[cols] < (Q1 - 1.5 * IQR)) |(df[cols] > (Q3 + 1.5 * IQR))).any(axis=1)]
df.boxplot()
df["Total"].value_counts()
plt.title('Grouped by Total')
sns.countplot(x="Total",data=df)
df["Payment"].value_counts()
plt.title('Grouped by Payment')
sns.countplot(x="Payment",data=df)
df["City"].value_counts()
plt.title('Grouped by City')
sns.countplot(x="City",data=df)
df["Product line"].value_counts()
plt.title('Grouped by Product line')
sns.countplot(x="Product line",data=df)
sns.displot(df["Quantity"])
sns.countplot(x="Gender",hue="Product line",data=df)
sns.countplot(x="Total",hue="Customer type",data=df)
pd.crosstab(df["Total"],df["Payment"])
pd.crosstab(df["Quantity"],df["City"])
df.corr()
sns.heatmap(df.corr(),annot=True)
```
OUPUT:
![1](https://user-images.githubusercontent.com/94169318/162870121-5b27daea-bd27-4e84-bfef-28a440d5e699.png)
![2](https://user-images.githubusercontent.com/94169318/162870214-9ae31f7d-6147-4ad1-90fe-f7a16f201e10.png)
![3](https://user-images.githubusercontent.com/94169318/162870240-61f2e228-1db0-4029-8542-0dc20bc0753d.png)
![4](https://user-images.githubusercontent.com/94169318/162870270-3b93acf4-f678-4c59-8231-2f55c548c990.png)
![5](https://user-images.githubusercontent.com/94169318/162870296-5476970c-2950-47eb-9484-249b3fb93e90.png)
![6](https://user-images.githubusercontent.com/94169318/162870325-c10e87a7-2878-4f0a-b4eb-e161677cbcb2.png)
![7](https://user-images.githubusercontent.com/94169318/162870350-54299f14-c326-4d25-a162-a501e9b431d2.png)
![8](https://user-images.githubusercontent.com/94169318/162870368-3e5e4eda-e51a-4952-9788-8e97321ec61f.png)
![9](https://user-images.githubusercontent.com/94169318/162870383-a4b699f0-a789-4c9c-9b01-e60f187d9dc5.png)
![10](https://user-images.githubusercontent.com/94169318/162870394-03fd1f2d-dc33-400a-8e4b-9f401d6a61f6.png)
![11](https://user-images.githubusercontent.com/94169318/162870438-ebafae21-773c-4800-b4ff-9555a7ae1252.png)
![12](https://user-images.githubusercontent.com/94169318/162870450-8fe1cb3d-eaa9-4a54-97b3-4dd5a6f83fda.png)
![13](https://user-images.githubusercontent.com/94169318/162870599-c6ab571a-567d-415c-9624-9bf6f8d612e5.png)
![14](https://user-images.githubusercontent.com/94169318/162870711-8cfae07d-ae7d-4911-acda-8fe4d7887b00.png)
![15](https://user-images.githubusercontent.com/94169318/162870698-eb10d2eb-13b4-4120-815c-a1ff843033e6.png)
![16](https://user-images.githubusercontent.com/94169318/162870722-2972ae42-574e-4dd3-ab9f-d1bd03ef3c9a.png)
![17](https://user-images.githubusercontent.com/94169318/162870742-f8f123e7-0c21-4b31-a726-2c8acbe77ef1.png)

## RESULT
The data has been cleaned, outlier has been removed and the EDA on the given data has been performed.
