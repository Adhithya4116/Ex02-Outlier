# Ex02-Outlier

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them

###Aim:
TO detect and remove the outliers in the given data set and save the final data.

##Algorithm:
Step 1:
Import the required packages(pandas,numpy,scipy)

Step 2:
Read the given csv file

Step3:
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

###Program:
(1) & (2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe.

(1) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe
```
Developed by :Adhithya Perumal.D
Reg.No: 212222230007

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

(3)Examine price_per_sqft column and use zscore of 3 to remove outliers.
```
from scipy import stats
z = np.abs(stats.zscore(df['price_per_sqft']))
df2 = df[(z<3)]
df2
print(df2.shape)
sns.boxplot(x="price_per_sqft",data=df2)
```

(4)(i) For the data set height_weight.csv detect weight outliers using IQR method.
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

(4)(ii) For the data set height_weight.csv detect height outliers using IQR method.
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

###OUTPUT:
(1)(2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe.
DATASET:
![ss](https://user-images.githubusercontent.com/118707079/230837057-239c07d9-8da2-4a49-9d43-6976cb31f091.png)
![ss2](https://user-images.githubusercontent.com/118707079/230837154-8747c2d7-e775-4d7b-a5fc-10c4d4c10233.png)

DATASET HEAD:
![ss3](https://user-images.githubusercontent.com/118707079/230837411-2a9beeec-f438-4b1c-99e5-d9a9227245e8.png)

DATASET INFO:
![ss4](https://user-images.githubusercontent.com/118707079/230837537-2ff984b4-429f-475b-b188-5aecf289e0b0.png)

DATASET DESCRIBE:
![ss5](https://user-images.githubusercontent.com/118707079/230837641-47064d37-2afc-4778-afdc-b9dbbe649c83.png)

NULL VALUE:
![ss6](https://user-images.githubusercontent.com/118707079/230837702-d351d7d8-a40b-4d3c-897e-52b79242d67c.png)

DATASHAPE:
![ss7](https://user-images.githubusercontent.com/118707079/230837763-a46f4159-fce6-41bd-b139-dec76a11e614.png)

BOX PLOT OF PRICE_PER_SQFT COLUMN WITH OUTLIER:
![ss8](https://user-images.githubusercontent.com/118707079/230837851-c623d6b1-1cbf-497d-bded-cee6761bbf6a.png)

price_per_sqft - Dataset after removing outliers:
![ss9](https://user-images.githubusercontent.com/118707079/230838011-80f4b026-fc3e-4c43-b9c8-f3ce31c5c700.png)

price_per_sqft - Shape of Dataset after removing outliers :
![ss10](https://user-images.githubusercontent.com/118707079/230838083-e798420c-0f2d-456c-acc2-9d821db9d5f2.png)

Box Plot of price_per_sqft column without outliers:
![ss11](https://user-images.githubusercontent.com/118707079/230838138-daaba88d-bdf3-4e88-ab04-33c6571154f1.png)

Examine price_per_sqft column and use zscore of 3 to remove outliers.
Dataset after removal of outlier using z score:
![ss12](https://user-images.githubusercontent.com/118707079/230838233-3dc19cc1-2bd3-46b0-b168-00d0ccc585bd.png)

Shape of Dataset after removal of outlier using z score:
![ss13](https://user-images.githubusercontent.com/118707079/230838322-2f912809-e210-4246-b1d5-e78fb05688c9.png)

(4) For the data set height_weight.csv detect weight and height outliers using IQR method:
Dataset:
![ss14](https://user-images.githubusercontent.com/118707079/230838410-169de914-45b5-456b-8bb6-c4b6859090f1.png)

Dataset Head:
![ss15](https://user-images.githubusercontent.com/118707079/230838472-37124425-d861-4fbf-9eaa-30fc1798ac08.png)

Dataset Info:
![ss16](https://user-images.githubusercontent.com/118707079/230838567-95132617-da96-44fd-b77d-4936ca57677c.png)

Dataset describe:
![ss17](https://user-images.githubusercontent.com/118707079/230838642-c5c748c7-59b9-4270-83bd-830109dec30f.png)

Nullvalues:
![ss18](https://user-images.githubusercontent.com/118707079/230838711-bb08c084-b116-48d0-be8e-0151ba056b3f.png)

Dataset shape:
![ss19](https://user-images.githubusercontent.com/118707079/230838800-6d7ab5ff-6963-4c3b-9fc2-1b78cde971f1.png)

Weight- with outliers:
![ss20](https://user-images.githubusercontent.com/118707079/230838859-58b141d8-90ba-4f2f-9206-0f03a67e55ea.png)

Weight - Dataset after removing Outliers using IQR method:
![ss21](https://user-images.githubusercontent.com/118707079/230839062-4a421d22-a880-4260-abfa-99ff9a958a58.png)

Weight - Shape of Dataset after removing Outliers using IQR method:
![ss23](https://user-images.githubusercontent.com/118707079/230839171-733f0f95-c04a-4240-ae5c-8e42d6520ecf.png)

Weight - Without Outliers using IQR method:
![ss22](https://user-images.githubusercontent.com/118707079/230839278-2fe839f2-3099-4709-82ee-bc2387757379.png)

Height - With outliers:
![s24](https://user-images.githubusercontent.com/118707079/230839421-32514a40-a3c2-4516-8685-f3fd6aeb043f.png)

Height - Dataset after removing Outliers using IQR method:
![s25](https://user-images.githubusercontent.com/118707079/230839508-e5571ea9-b15c-40fb-98c5-4918405da630.png)

Height - Shape of Dataset after removing Outliers using IQR method:
![s26](https://user-images.githubusercontent.com/118707079/230839579-13399d65-ed57-44bc-9f2c-e83e1ec4edb3.png)

Height - Without Outliers using IQR method:
![s277](https://user-images.githubusercontent.com/118707079/230839645-90ffdad3-b61a-4e7d-8551-5625e8b09564.png)


###Result:

Thus the outliers are detected and removed in the given file and the final data set is saved into the file.







