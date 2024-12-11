## EXNO-3-DS

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set.
STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING AND OUTPUT:
from google.colab import drive

drive.mount('/content/drive')

import pandas as pd

import numpy as np

import matplotlib.pyplot as plt

import seaborn as sns

![image](https://github.com/user-attachments/assets/d270825a-f546-447f-abd1-cc6e3a76da3f)

ls drive/MyDrive/'Colab Notebooks'/Data_set.csv

![image](https://github.com/user-attachments/assets/cb925a94-c76a-48b9-b45a-bd95317c76d3)

ls drive/MyDrive/'Colab Notebooks'/Data_to_Transform.csv

![image](https://github.com/user-attachments/assets/ebb89d99-d32d-41f3-b883-718accbeea7b)

ls drive/MyDrive/'Colab Notebooks'/'Encoding Data.csv'

![image](https://github.com/user-attachments/assets/01ea8c11-b98e-412d-af86-bd016ee36bb6)

df=pd.read_csv('drive/MyDrive/Colab Notebooks/Encoding Data.csv')

df

![image](https://github.com/user-attachments/assets/511bcf8d-90a6-40eb-8221-4e6d2fbe5117)

ORDINAL ENCODER

from sklearn.preprocessing import LabelEncoder,OrdinalEncoder

pm=['Hot','Warm','Cold']

e1=OrdinalEncoder(categories=[pm])

e1.fit_transform(df[["ord_2"]])

![image](https://github.com/user-attachments/assets/1f93d1da-c790-4817-927c-22c388879ea5)

df['bo2']=e1.fit_transform(df[["ord_2"]])

df

![image](https://github.com/user-attachments/assets/a4350b91-f307-44ab-9e54-c7fb75fad35f)

LABEL ENCODER

le=LabelEncoder()

dfc=df.copy()

dfc['ord_2']=le.fit_transform(df[["ord_2"]])

dfc

![image](https://github.com/user-attachments/assets/17d1d943-1e83-490a-b916-cc29710e85ae)

ONEHOT ENCODER


from sklearn.preprocessing import OneHotEncoder

ohe=OneHotEncoder()

df2=df.copy()

enc=pd.DataFrame(ohe.fit_transform(df2[['nom_0']]))

df2=pd.concat([df2,enc],axis=1)

df2

![image](https://github.com/user-attachments/assets/0b01f6be-27f0-45c5-b716-65c7de6bc9ed)

pd.get_dummies(df2,columns=["nom_0"])

![image](https://github.com/user-attachments/assets/ee7dd2d3-3300-4541-bdda-f1de8e6fc8c2)

BINARY ENCODER

pip install --upgrade category_encoders

![image](https://github.com/user-attachments/assets/66069596-0a6d-4b35-a3ca-57ccb684d5c8)

from category_encoders import BinaryEncoder

df=pd.read_csv('drive/MyDrive/data.csv')

df

dfb=pd.concat([df,nd],axis=1)

dfb

![image](https://github.com/user-attachments/assets/848fd5f1-a5fb-4406-a36e-f109dac8b094)


TARGET ENCODER

from category_encoders import TargetEncoder

te=TargetEncoder()

cc=df.copy()

new=te.fit_transform(X=cc["City"],y=cc["Target"])

cc=pd.concat([cc,new],axis=1)

cc

![image](https://github.com/user-attachments/assets/64082181-bcc2-430c-9f42-a476157b92b7)

FEATURE TRANSFORMATION

from scipy import stats

df=pd.read_csv('drive/MyDrive/Data_to_Transform.csv')

df

![image](https://github.com/user-attachments/assets/c1a124de-ab39-40b1-8d9a-e57415fe583b)

df.skew()

![image](https://github.com/user-attachments/assets/2ed57179-30bf-4aa5-b9e5-b8fe88826ad1)

np.log(df["Highly Positive Skew"])  

![image](https://github.com/user-attachments/assets/a205734e-d02e-49ef-a7c4-ad41e596bb92)

np.reciprocal(df["Moderate Positive Skew"])

![image](https://github.com/user-attachments/assets/0af9c29b-6a54-44bc-b495-57f51be98fa4)

np.sqrt(df["Highly Positive Skew"])

![image](https://github.com/user-attachments/assets/65765c70-51e3-4946-b3c4-641d1d2d67d6)

np.square(df["Highly Positive Skew"])

![image](https://github.com/user-attachments/assets/b748d6cd-32ad-418f-a2d1-0c19a8460665)

df["Highly Positive Skew_boxcox"],parameters=stats.boxcox(df["Highly Positive Skew"])

df

![image](https://github.com/user-attachments/assets/9afe082b-0865-4bc1-b9a0-c1d0b813b88e)

df["Moderate Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Moderate Negative Skew"])

df

![image](https://github.com/user-attachments/assets/9c07f73e-d29b-4f35-afd4-32c95f652764)

df.skew()

![image](https://github.com/user-attachments/assets/f7d96adb-7049-4b4b-9684-b6228d2dca02)

import seaborn as sns

import statsmodels.api as sm

import matplotlib.pyplot as plt

sm.qqplot(df["Moderate Negative Skew"],line='45')

plt.show()

![image](https://github.com/user-attachments/assets/4935b51c-447f-467a-bad3-9328dc93dc1f)

sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')

plt.show()

![image](https://github.com/user-attachments/assets/73685f29-81c8-44b9-bf32-363086485883)


# RESULT:
THUS THE ABOVE CODE IS EXECUETED SUCCESSFULLY

