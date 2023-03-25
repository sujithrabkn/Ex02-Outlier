# Ex02-Outlier

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them

##Aim:

###To detect and remove the outliers in the given data set and save the final data.

##Algorithm:

##Step 1:

###Import the required packages(pandas,numpy,scipy).

##Step 2:

###Read the given csv file.

##Step 3:

###Convert the file into a dataframe and get information of the data.

##Step 4:

###Remove the non numerical data columns using drop() method.

##Step 5:

###Detect the outliers in the data set using z scores method.

##Step 6:

###Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)

##Step 7:

###Check if the outliersare removed from data set using graphical methods.

##Step 8:

###Save the final data set into the file.

##Program:

##1)& (2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe.

```
Program developed by : SUJITHRA B K N

Register number : 212222230153

import pandas as pd

import numpy as np

import seaborn as sns

df = pd.read_csv("/content/bhp.csv")

df

df.head()

df.describe()

df.info()

df.isnull().sum()

df.shape

sns.boxplot(x="price_per_sqft",data=df)

q1 = df['price_per_sqft'].quantile(0.25)

q3 = df['price_per_sqft'].quantile(0.75)

print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1

ul = q3+1.5*IQR

ll = q1-1.5*IQR

df1 =df[((df['price_per_sqft']>=ll)&(df['price_per_sqft']<=ul))]

df1

df1.shape

sns.boxplot(x="price_per_sqft",data=df1)
```

##(3)Examine price_per_sqft column and use zscore of 3 to remove outliers.

```
from scipy import stats

z = np.abs(stats.zscore(df['price_per_sqft']))

df2 = df[(z<3)]

df2

print(df2.shape)

sns.boxplot(x="price_per_sqft",data=df2)
```

##(4)(i) For the data set height_weight.csv detect weight outliers using IQR method.

```
import pandas as pd

import numpy as np

import seaborn as sns

df = pd.read_csv("/content/height_weight - Sheet1.csv")

df

df.head()

df.info()

df.describe()

df.isnull().sum()

df.shape

print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1

ul = q3+1.5*IQR

ll = q1-1.5*IQR

df1 =df[((df['weight']>=ll)&(df['weight']<=ul))]

df1

df1.shape

sns.boxplot(x="weight",data=df1)
```

##(4)(ii) For the data set height_weight.csv detect height outliers using IQR method.

```
sns.boxplot(x="height",data=df)

q1 = df['height'].quantile(0.25)

q3 = df['height'].quantile(0.75)

print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1

ul = q3+1.5*IQR

ll = q1-1.5*IQR

df2 =df[((df['height']>=ll)&(df['height']<=ul))]

df2

df2.shape

sns.boxplot(x="height",data=df2)
```

##Output:

##(1)(2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe.

##Dataset:

![Screenshot (24)](https://user-images.githubusercontent.com/119477857/227693222-847854a5-3708-4d81-bedb-90c0a98f15b1.png)

##Dataset Head :

![Screenshot (25)](https://user-images.githubusercontent.com/119477857/227693381-2a4d50e1-2b1c-404b-9cb4-7166d7f692b5.png)

##Dataset Info :

![Screenshot (27)](https://user-images.githubusercontent.com/119477857/227693518-1caf776f-fffe-4914-8c4d-8cdaebcfe46b.png)

##Dataset Describe:

![Screenshot (26)](https://user-images.githubusercontent.com/119477857/227693625-43b677fd-bedf-4edf-b735-098727dc1e18.png)

##Null Values:

![Screenshot (28)](https://user-images.githubusercontent.com/119477857/227693737-70e0a083-b32d-4be8-b6a4-b426a1aa24c9.png)

##Dataset Shape:

![Screenshot (29)](https://user-images.githubusercontent.com/119477857/227693834-9b0c7156-3466-4884-b9f6-4ed82250eba3.png)

##Box plot of price_per_sqft column with outliers:

![Screenshot (30)](https://user-images.githubusercontent.com/119477857/227693941-8af73f15-fe3d-416d-a812-e9ea47649945.png)

##price_per_sqft - Dataset after removing outliers:

![Screenshot (31)](https://user-images.githubusercontent.com/119477857/227694093-d3dce197-ba59-4687-9670-712f4ace1b9d.png)

##price_per_sqft - Shape of Dataset after removing outliers :

![Screenshot (32)](https://user-images.githubusercontent.com/119477857/227694301-d2023619-9b9c-47c4-a043-4c8b17823b1f.png)

##Box Plot of price_per_sqft column without outliers:

![Screenshot (33)](https://user-images.githubusercontent.com/119477857/227694415-28ef0bd0-d1fb-4ec8-8bc1-2aa35cad4dd5.png)

##(3) Examine price_per_sqft column and use zscore of 3 to remove outliers.

##Dataset after removal of outlier using z score:

![Screenshot (34)](https://user-images.githubusercontent.com/119477857/227694565-3c292510-b365-436c-a63a-895958d91dec.png)

##Shape of Dataset after removal of outlier using z score:

![Screenshot (35)](https://user-images.githubusercontent.com/119477857/227694697-3bd71cc9-6a50-4e90-9ba7-3e6d7566b0be.png)

![Screenshot (36)](https://user-images.githubusercontent.com/119477857/227694877-899405e7-95d6-4bb9-aece-95434c3ec83d.png)

##(4) For the data set height_weight.csv detect weight and height outliers using IQR method:

![Screenshot (37)](https://user-images.githubusercontent.com/119477857/227695008-716db499-62ff-4bf3-8d26-e258effcf18f.png)

##Dataset Head:

![Screenshot (38)](https://user-images.githubusercontent.com/119477857/227695128-38c64371-56b4-4097-a9af-7929612c59f8.png)

##Dataset Info:

![Screenshot (39)](https://user-images.githubusercontent.com/119477857/227695218-79b4ea51-43f1-404a-8d92-0cb7c2a8075a.png)

##Dataset Describe:

![Screenshot (40)](https://user-images.githubusercontent.com/119477857/227695311-8302cdf7-157a-421c-82c6-6f34ae52cbb3.png)

##Null Values:

![Screenshot (41)](https://user-images.githubusercontent.com/119477857/227695397-22f8322e-6e4c-4541-9a88-17e7e954e9f8.png)

##Dataset Shape:

![Screenshot (42)](https://user-images.githubusercontent.com/119477857/227695436-38064283-b403-4487-b831-155f93d874c6.png)

##Weight - With outliers:

![Screenshot (43)](https://user-images.githubusercontent.com/119477857/227695446-527b0d90-1e3a-4d3c-9fc1-dc0aea62e66d.png)

##Weight - Dataset after removing Outliers using IQR method:

![Screenshot (44)](https://user-images.githubusercontent.com/119477857/227695466-ff7dfd02-da83-4e05-8963-20ec9608eb64.png)

##Weight - Shape of Dataset after removing Outliers using IQR method:

![Screenshot (45)](https://user-images.githubusercontent.com/119477857/227695474-1a080931-5157-4050-a37d-d45f5da5d920.png)

##Weight - Without Outliers using IQR method:

![Screenshot (46)](https://user-images.githubusercontent.com/119477857/227695485-e6104496-637f-4516-9a65-1638c460b59d.png)

##Height - With outliers:

![Screenshot (47)](https://user-images.githubusercontent.com/119477857/227695494-fa2e136d-9bab-47b3-a60e-205be4445b2b.png)

##Height - Dataset after removing Outliers using IQR method:

![Screenshot (48)](https://user-images.githubusercontent.com/119477857/227695507-de334657-4518-4551-a1d2-6d69670a8a83.png)

##Height - Shape of Dataset after removing Outliers using IQR method:

![Screenshot (49)](https://user-images.githubusercontent.com/119477857/227695522-33e691bb-3875-40d5-8436-8ae2e85319f7.png)

##Height - Without Outliers using IQR method:

![Screenshot (50)](https://user-images.githubusercontent.com/119477857/227695537-4788ea77-4345-447d-8c8d-2c7ee87b2660.png)

##Result:

###Thus the outliers are detected and removed in the given file and the final data set is saved into the file.
