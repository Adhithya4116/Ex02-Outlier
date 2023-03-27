# Ex02-Outlier

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them

AIM:
TO detect and remove the outliers in the given data set and save the final data.

Algorithm:

Step 1:
Import the required packages(pandas,numpy,scipy)

Step 2:
Read the given csv file

Step 3:
Convert the file into a dataframe and get information of the data.

Step 4:
Remove the non numerical data columns using drop() method.

Step 5:
Detect the outliers in the data set using z scores method.

Step 6:
Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)

Step 7:
Check if the outliersare removed from data set using graphical methods.

Step 8:
Save the final data set into the file.

Program:

(1) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe
```
Developed by :Adhithya Perumal.D
Reg.No: 212222230007

import pandas as pd
import seaborn as sns
df = pd.read_csv("/content/bhp.csv")
df
sns.boxplot(data=df)
sns.boxplot(x="price_per_sqft",data=df)
q1 = df['price_per_sqft'].quantile(0.35)
q3 = df['price_per_sqft'].quantile(0.65)
print("First Quantile =",q1,"\nSecond Quantile =",q3)
IQR = q3-q1
high = q3+1.5*IQR
low = q1-1.5*IQR
df1 =df[((df['price_per_sqft']>=low)&(df['price_per_sqft']<=high))]
df1
sns.boxplot(x="price_per_sqft",data=df1)
df1.shape
```

(1) & (2) Examine price_per_sqft column and use zscore of 3 to remove outliers.
```
from scipy import stats
import numpy as np
z = np.abs(stats.zscore(df['price_per_sqft']))
df2 = df[(z<3)]
df2
df2.shape
sns.boxplot(x="price_per_sqft",data=df2)
```

(4) (i)For the data set height_weight.csv detect weight outliers using IQR method
```
df3 = pd.read_csv("/content/height_weight.csv")
df3
sns.boxplot(x="weight",data=df3)
q1 = df3["weight"].quantile(0.25)
q3 = df3['weight'].quantile(0.75)
print("First Quantile = ",q1,"\nSecond Quantile = ",q3)
IQR = q3-q1
low = q1-1.5*IQR
high = q3+1.5*IQR
df4 =df3[((df3['weight']>=low)&(df3['weight']<=high))]
df4
df4.shape
sns.boxplot(x="weight",data=df4)
```

(4)(ii) For the data set height_weight.csv detect height outliers using IQR method.
```
sns.boxplot(x="height",data=df3)
q1 = df3["height"].quantile(0.25)
q3 = df3['height'].quantile(0.75)
print("First Quantile = ",q1,"\nSecond Quantile = ",q3)
IQR = q3-q1
low = q1-1.5*IQR
high = q3+1.5*IQR
df5 =df3[((df3['height']>=low)&(df3['height']<=high))]
df5
df5.shape
sns.boxplot(x="height",data=df5)
```

OUTPUT:

DATASET FOR bhp.csv:

![dataset](https://user-images.githubusercontent.com/118707079/227997961-7260f594-29ea-4f5f-8ef5-c621656a47bf.png)

bhp Boxplot:

![bhp](https://user-images.githubusercontent.com/118707079/227998209-74597706-0dc6-454b-b92f-1173b59fa3cf.png)

DATASET BOXPLOT WITH OUTLIERS(BHP):

![dataset boxplot](https://user-images.githubusercontent.com/118707079/227998525-5b8baee2-72dc-489a-96ed-b0f28b361b28.png)

DATASET WITHOUT OUTLIERS(BHP):

![outliers](https://user-images.githubusercontent.com/118707079/227998834-3b8fe8d7-c0a7-4e84-a636-fe2147f22408.png)

DATASET BOXPLOT WITHOUT OUTLIERS(BHP):

![6](https://user-images.githubusercontent.com/118707079/227999004-a54c3ba0-be94-4f48-b7f7-42ce19c0aaa3.png)

Shape:

![shape](https://user-images.githubusercontent.com/118707079/227999153-9e6672c5-45ca-407c-91f4-9f5992b8dbc1.png)

DATASET AFTER REMOVAL OF OUTLIERS USING Z-SCORE(BHP):

![after](https://user-images.githubusercontent.com/118707079/227999547-4a8ac64a-5346-4976-a8ea-8f525cefa766.png)

Shape:

![shp](https://user-images.githubusercontent.com/118707079/227999897-c5254b81-305c-43be-a115-913e1ef60d20.png)

DATASET BOXPLOT AFTER REMOVAL OF OUTLIERS USING Z-SCORE(BHP):

![z score](https://user-images.githubusercontent.com/118707079/228000012-b149724f-e3ee-4091-b626-0bfa7b09b0d9.png)

DATASET FOR WEIGHT_HEIGHT_CSV:

![heightweight](https://user-images.githubusercontent.com/118707079/228000218-953d99b9-3de4-49f0-b768-fc228ce25baf.png)

DATASET BOXPLOT WITH OUTLIERS(WEIGHT_HEIGHT):

![datas](https://user-images.githubusercontent.com/118707079/228000454-b4d3d67d-89c3-4928-9518-00e063c9c3ab.png)

DATASET AFTER REMOVING OUTLIERS USING IQR METHOD(WEIGHT_HEIGHT):

![weight](https://user-images.githubusercontent.com/118707079/228000770-c6eccf91-62ad-4be2-9077-5f5cce45888a.png)

DATASET BOXPLOT AFTER REMOVING OUTLIERS USING IQR METHOD(WEIGHT_HEIGHT):

![after data](https://user-images.githubusercontent.com/118707079/228000926-7c51700c-9fb7-4b16-b7c2-542babcf7f8e.png)

FOR HEIGHT COLUMN WITH OUTLIERS:

![hgt](https://user-images.githubusercontent.com/118707079/228001086-16fbba76-bd77-433a-b16e-c52931af5d47.png)

![wgt](https://user-images.githubusercontent.com/118707079/228001332-9592d92b-71cb-4b04-b26b-2135f37b5bec.png)

AFTER REMOVING OUTLIERS BOXPLOT FOR HEIGHT:

![dd](https://user-images.githubusercontent.com/118707079/228001710-ce4f97c5-3594-4e20-b128-4944d1f5d5c9.png)

Result:

Thus the outliers are detected and removed in the given file and the final data set is saved into the file.







