Importing Packages
import numpy as np
import pandas as pd 
import matplotlib.pyplot as plt
import seaborn as sb
%matplotlib inline

Import of the CSV file
df=pd.read_csv("../input/stores-area-and-sales-data/Stores.csv")

Top 5 rows of the data
df.head()

output :

Store ID	Store_Area	Items_Available	Daily_Customer_Count	Store_Sales
1	1659	1961	530	66490
2	1461	1752	210	39820
3	1340	1609	720	54010
4	1451	1748	620	53730
5	1770	2111	450	46620

df.info()

output:
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 896 entries, 0 to 895
Data columns (total 5 columns):
 #   Column                Non-Null Count  Dtype
---  ------                --------------  -----
 0   Store ID              896 non-null    int64
 1   Store_Area            896 non-null    int64
 2   Items_Available       896 non-null    int64
 3   Daily_Customer_Count  896 non-null    int64
 4   Store_Sales           896 non-null    int64
dtypes: int64(5)
memory usage: 35.1 KB


Finding out the number of empty cells in the dataset

df.isnull().sum()

output:
Store ID                0
Store_Area              0
Items_Available         0
Daily_Customer_Count    0
Store_Sales             0
dtype: int64
There exists no empty cells in the dataset

Descriptive Statistics of the Dataset

df.describe()

Conducting z test to find out outliers
We have assumed the data to be normal and to prove its normality, we are conducting the z test.
x=df["Store_Sales"]
mean=df["Store_Sales"].mean()
std=df["Store_Sales"].std()
z= (x-mean)/std
z
output:

0      0.415264
1     -1.136153
2     -0.310708
3     -0.326996
4     -0.740591
         ...   
891    0.409447
892    1.322147
893    0.994064
894    2.167370
895   -0.291512
Name: Store_Sales, Length: 896, dtype: float64

Density curve showing the frequency of number of items present in each store

ax=plt.figure(figsize=(10,6))
sb.distplot(df["Items_Available"],color="blue",bins=100)

 

Scatterplot between the Store Area and Items Available

ax=plt.figure(figsize=(10,6))
sb.scatterplot(x='Store_Area',y='Items_Available',data=df,color="green")




 

Scatterplot between the Store Sales and Items Available

ax=plt.figure(figsize=(10,6))
sb.scatterplot(x='Store_Sales',y='Items_Available',data=df,color="orange")


 

Scatterplot between the Store Sales and Daily Customer Count

ax=plt.figure(figsize=(10,6))
sb.scatterplot(x='Store_Sales',y='Daily_Customer_Count',data=df,color="brown")

 
Correlation of the different variables

ax=plt.figure(figsize=(10,6))
corr=df.corr()
sb.heatmap(corr,linewidths=1,linecolor='white',annot=True)

