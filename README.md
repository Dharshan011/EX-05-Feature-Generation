# EX-05-Feature-Generation


## AIM
To read the given data and perform Feature Generation process and save the data to a file. 

# Explanation
Feature Generation (also known as feature construction, feature extraction or feature engineering) is the process of transforming features into new features that better relate to the target.
 

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature Generation techniques to all the feature of the data set
### STEP 4
Save the data to the file


# CODE
 ## data:
 ```
 import pandas as pd
df=pd.read_csv("data.csv")
print(df)
import category_encoders as ce
be=ce.BinaryEncoder()
df1=be.fit_transform(df["bin_1"])
df["bin_1"] = be.fit_transform(df["bin_1"])
df1
be=ce.BinaryEncoder()
df2=be.fit_transform(df["bin_2"])
df["bin_2"] = be.fit_transform(df["bin_2"])
df2
df1=df.copy()
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder,OneHotEncoder
import category_encoders as ce
be=ce.BinaryEncoder()
ohe=OneHotEncoder(sparse=False)
le=LabelEncoder()
oe=OrdinalEncoder()
df1["City"] = ohe.fit_transform(df1[["City"]])
temp=['Cold','Warm','Hot','Very Hot']
oe1=OrdinalEncoder(categories=[temp])
df1['Ord_1'] = oe1.fit_transform(df1[["Ord_1"]])
edu=['High School','Diploma','Bachelors','Masters','PhD']
oe2=OrdinalEncoder(categories=[edu])
df1['Ord_2']= oe2.fit_transform(df1[["Ord_2"]])
df1
## SCALING:
from sklearn.preprocessing import MinMaxScaler
sc=MinMaxScaler()
df2=pd.DataFrame(sc.fit_transform(df1),columns=(['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target']))
df2
from sklearn.preprocessing import StandardScaler
sc1=StandardScaler()
df3=pd.DataFrame(sc1.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df3
from sklearn.preprocessing import MaxAbsScaler
sc2=MaxAbsScaler()
df4=pd.DataFrame(sc2.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df4
from sklearn.preprocessing import RobustScaler
sc3=RobustScaler()
df5=pd.DataFrame(sc3.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df5
```
Encoding data:

```import pandas as pd
df=pd.read_csv("Encoding Data.csv")
df
## GENERATION
import category_encoders as ce
be=ce.BinaryEncoder()
ndf=be.fit_transform(df["bin_1"])
df["bin_1"] = be.fit_transform(df["bin_1"])
ndf
be=ce.BinaryEncoder()
ndf2=be.fit_transform(df["bin_2"])
df["bin_2"] = be.fit_transform(df["bin_2"])
ndf2
df1=df.copy()
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
le=LabelEncoder()
oe=OrdinalEncoder()
df1["nom_0"] = oe.fit_transform(df1[["nom_0"]])
temp=['Cold','Warm','Hot']
oe2=OrdinalEncoder(categories=[temp])
df1['ord_2'] = oe2.fit_transform(df1[['ord_2']])
df1
## SCALING:
from sklearn.preprocessing import MinMaxScaler
sc=MinMaxScaler()
df0=pd.DataFrame(sc.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
df0
from sklearn.preprocessing import StandardScaler
sc1=StandardScaler()
df2=pd.DataFrame(sc1.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
df2
from sklearn.preprocessing import MaxAbsScaler
sc2=MaxAbsScaler()
df3=pd.DataFrame(sc2.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
df3
from sklearn.preprocessing import RobustScaler
sc3=RobustScaler()
df4=pd.DataFrame(sc3.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
df4

```
Titanic Dataset:
```import pandas as pd
df=pd.read_csv("titanic_dataset.csv")
df
df.drop("Name",axis=1,inplace=True)
df.drop("Ticket",axis=1,inplace=True)
df.drop("Cabin",axis=1,inplace=True)
df.isnull().sum()

df["Age"]=df["Age"].fillna(df["Age"].median())
df["Embarked"]=df["Embarked"].fillna(df["Embarked"].mode()[0])
df.isnull().sum()
df
## ENCODING
import category_encoders as ce
be=ce.BinaryEncoder()
ndf=be.fit_transform(df['Sex'])
ndf
df1=df.copy()
from sklearn.preprocessing import LabelEncoder, OrdinalEncoder
embark=['S','C','Q']
e1=OrdinalEncoder(categories=[embark])
df1['Embarked'] = e1.fit_transform(df[['Embarked']])
df1

## SCALING
from sklearn.preprocessing import MinMaxScaler
sc=MinMaxScaler()
df0=pd.DataFrame(sc.fit_transform(df1),columns=['PassengerId', 'Survived', 'Pclass', 'Sex','Age','SibSp','Parch','Fare','Embarked'])
df0
from sklearn.preprocessing import StandardScaler
sc1=StandardScaler()
df2=pd.DataFrame(sc1.fit_transform(df1),columns=['PassengerId', 'Survived', 'Pclass', 'Sex','Age','SibSp','Parch','Fare','Embarked'])
df2
from sklearn.preprocessing import MaxAbsScaler
sc2=MaxAbsScaler()
df3=pd.DataFrame(sc2.fit_transform(df1),columns=['PassengerId', 'Survived', 'Pclass', 'Sex','Age','SibSp','Parch','Fare','Embarked'])
df3
from sklearn.preprocessing import RobustScaler
sc3=RobustScaler()
df4=pd.DataFrame(sc3.fit_transform(df1),columns=['PassengerId', 'Survived', 'Pclass', 'Sex','Age','SibSp','Parch','Fare','Embarked'])
df4


```

# OUPUT
## data
![Screenshot 2023-05-10 121605](https://github.com/Dharshan011/EX-05-Feature-Generation/assets/113497491/5ca21b59-72dc-433b-92bb-3300a23a4c55)

![Screenshot 2023-05-10 121611](https://github.com/Dharshan011/EX-05-Feature-Generation/assets/113497491/0c

![Screenshot 2023-05-10 121618](https://github.com/Dharshan011/EX-05-Feature-Generation/assets/113497491/8b4e96eb-d818-4265-a265-6585c95642c1)
e88daf-5fbe-4b84-b8eb-a13e4497f398)

![Screenshot 2023-05-10 121625](https://github.com/Dharshan011/EX-05-Feature-Generation/assets/113497491/28ca814e-6e84-4b39-b85d-9de8f47ed8c6)

![Screenshot 2023-05-10 121635](https://github.com/Dharshan011/EX-05-Feature-Generation/assets/113497491/bc69dba3-402d-4261-b84e-33660d5c34f2)

![Screenshot 2023-05-10 121643](https://github.com/Dharshan011/EX-05-Feature-Generation/assets/113497491/42ceb7d3-f0c7-4163-ba32-e6bb8e40c9b6)

![Screenshot 2023-05-10 121651](https://github.com/Dharshan011/EX-05-Feature-Generation/assets/113497491/28e0ed5b-313f-42d6-977f-837fe8b0ba4e)

![Screenshot 2023-05-10 121657](https://github.com/Dharshan011/EX-05-Feature-Generation/assets/113497491/8cf47154-cd58-4593-8682-c1d13d526e03)


![Screenshot 2023-05-10 121703](https://github.com/Dharshan011/EX-05-Feature-Generation/assets/113497491/944891e0-9df9-4cb7-be2c-00aed942d9aa)

![Screenshot 2023-05-10 121710](https://github.com/Dharshan011/EX-05-Feature-Generation/assets/113497491/faa9468a-ad02-433d-a585-c9563de37d47)

![Screenshot 2023-05-10 121716](https://github.com/Dharshan011/EX-05-Feature-Generation/assets/113497491/47c687f0-352b-4260-ad48-48a0bd05b60e)


![Screenshot 2023-05-10 121722](https://github.com/Dharshan011/EX-05-Feature-Generation/assets/113497491/916f1336-058c-49fc-95d4-bca0fdb931a6)

![Screenshot 2023-05-10 121730](https://github.com/Dharshan011/EX-05-Feature-Generation/assets/113497491/1c7f7a8c-10ae-4c9e-b291-09945c5e552f)


![Screenshot 2023-05-10 121735](https://github.com/Dharshan011/EX-05-Feature-Generation/assets/113497491/285b92d3-c342-432c-9d53-8d2e342b8c04)

![Screenshot 2023-05-10 121740](https://github.com/Dharshan011/EX-05-Feature-Generation/assets/113497491/fdcdaa13-0f3f-4d1d-8951-bfb1270b28ef)

![Screenshot 2023-05-10 121748](https://github.com/Dharshan011/EX-05-Feature-Generation/assets/113497491/e79622f5-808e-46bb-85b0-d451d490b8f2)

![Screenshot 2023-05-10 121752](https://github.com/Dharshan011/EX-05-Feature-Generation/assets/113497491/5c49c102-e646-4c5b-a38d-de0e8504ba1e)

![Screenshot 2023-05-10 121801](https://github.com/Dharshan011/EX-05-Feature-Generation/assets/113497491/6ca1d64d-0422-4d8e-a2ce-b8a2a40fab26)

![Screenshot 2023-05-10 121806](https://github.com/Dharshan011/EX-05-Feature-Generation/assets/113497491/fd899d47-82ed-417a-9d98-294054478294)
![Screenshot 2023-05-10 121814](https://github.com/Dharshan011/EX-05-Feature-Generation/assets/113497491/6e2ec0f5-be80-431b-90d3-87084459360c)



![Screenshot 2023-05-10 121820](https://github.com/Dharshan011/EX-05-Feature-Generation/assets/113497491/7a3e1a27-b52c-4400-a069-d5173012d5b8)



![Screenshot 2023-05-10 121826](https://github.com/Dharshan011/EX-05-Feature-Generation/assets/113497491/8b6bbfb1-89f9-47b2-a630-d174ea9fb180)



![Screenshot 2023-05-10 121832](https://github.com/Dharshan011/EX-05-Feature-Generation/assets/113497491/7ab7a2da-fdf1-42b0-aba5-9efa01461e49)
##Result:
Thus the Feature Generation and Feature Scaling process is applied to the given data set
