# Data Cleaning
#My first Numpy/Pandas code to clean data!

import numpy as np
import pandas as pd

# Importing file and creating a DataFrame
dataframe = pd.read_csv("workout_20000.csv")
dataframe.head()

#Checking empty values
pd.core.frame.DataFrame
print(dataframe.info())
print((dataframe.isnull().sum(axis = 0)))

#Removing empty values
dataframe.dropna(inplace=True)

#Checking if empty values are deleted successfully
dataframe.info()


#Checking worng format
dataframe.dtypes

#Removing not integer type:
for d in dataframe.index:
    if (dataframe.loc[d,'Duration'].isnumeric() == False):
        dataframe.drop(d,inplace=True)

dataframe['Duration'] = pd.to_numeric(dataframe['Duration'])

for d in dataframe.index:
    if (dataframe.loc[d,'Calories'].isnumeric() == False):
        dataframe.drop(d,inplace=True)

dataframe['Calories'] = pd.to_numeric(dataframe['Calories'])

dataframe.dtypes


#Removing duplicates:
dataframe[dataframe.duplicated() == True]
dataframe.drop_duplicates(inplace=True)

len(dataframe[dataframe.duplicated() == True])

#Removing wrong data:
for d in dataframe.index:
    if (dataframe.loc[d,"Duration"] > 250) or (dataframe.loc[d,"Duration"] < 10) or (dataframe.loc[d,"Pulse"] > 140) or (dataframe.loc[d,"Pulse"] < 80) or (dataframe.loc[d,"Max Pulse"] > 160) or (dataframe.loc[d,"Max Pulse"] < 120) or (dataframe.loc[d,"Calories"] > 1750) or (dataframe.loc[d,"Calories"] < 50):
        dataframe.drop(d, inplace=True)


#Finding correlations:x
print(dataframe.corr())
dataframe['Calories'] = pd.to_numeric(dataframe['Calories'])

dataframe.dtypes


###Removing duplicates:
dataframe[dataframe.duplicated() == True]
dataframe.drop_duplicates(inplace=True)

len(dataframe[dataframe.duplicated() == True])

###Removing wrong data:
for d in dataframe.index:
    if (dataframe.loc[d,"Duration"] > 250) or (dataframe.loc[d,"Duration"] < 10) or (dataframe.loc[d,"Pulse"] > 140) or (dataframe.loc[d,"Pulse"] < 80) or (dataframe.loc[d,"Max Pulse"] > 160) or (dataframe.loc[d,"Max Pulse"] < 120) or (dataframe.loc[d,"Calories"] > 1750) or (dataframe.loc[d,"Calories"] < 50):
        dataframe.drop(d, inplace=True)


###Finding correlations:x
print(dataframe.corr())
