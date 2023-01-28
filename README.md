# Animation
This describe about how numpy, pandas and data visualization are applied in a dataset. Here I have used a anime dataset .Lets see the most used attributes, methods and  operation in numpy and pandas.

Numpy

NumPy is a Python library used for working with arrays.

In Python we have lists that serve the purpose of arrays, but they are slow to process.

NumPy aims to provide an array object that is up to 50x faster than traditional Python lists.

The array object in NumPy is called ndarray, it provides a lot of supporting functions that make working with ndarray very easy.

Arrays are very frequently used in data science, where speed and resources are very important.

Pandas

Pandas is a Python library.

We can load and retrieve data.

Pandas is used to analyze data.

Data Visualization

Python provides various libraries that come with different features for visualizing data. All these libraries come with different features and can support various types of graphs. In this tutorial, we will be discussing two such libraries.

Matplotlib

Matplotlib is an easy-to-use, low-level data visualization library that is built on NumPy arrays. It consists of various plots like scatter plot, line plot, histogram, etc. Matplotlib provides a lot of flexibility. 

Seaborn

Seaborn is a high-level interface built on top of the Matplotlib. It provides beautiful design styles and color palettes to make more attractive graphs.

Dataset
https://www.kaggle.com/datasets/vishalmane10/anime-dataset-2022












import pandas as pd
import numpy as np
import matplotlib.pyplot as plt 
import seaborn as sns

#Load dataset
data=pd.read_csv("Anime.csv")

#To see first 5 rows of the DataFrame
data.head()

#To see last 5 rows of the DataFrame
data.tail()

#To find no of rows & columns 
data.shape

#To find total cell count
data.size

#To find Dimension
data.ndim

#To find column names
data.columns

#To find information about the DataFrame
data.info()

#To find min,max,count,etc...
data.describe()

#Slicing of rows
data.loc[75:85]

#To find the total count of a specific variable
data["Type"].value_counts()

print("Mean Value : ",data[data["Release_season"]=="Spring"]["Episodes"].mean())
print("Median Value : ",data[data["Release_season"]=="Spring"]["Episodes"].median())
print("Count : ",data[data["Release_season"]=="Spring"]["Episodes"].count())

print("Mean Value : ",data.groupby("Type")["Episodes"].mean())

#Sort value based upon some condition
data.sort_values(["Episodes","Release_year"],ascending=False)

data.groupby("Release_season")["Rating"].agg(["mean","median","count","max","min"])

plt.figure(figsize=(12,12))
plt.title("Visualization of Animation")
plt.xlabel("Type of Shows")
plt.ylabel("Ratings")
plt.plot(data["Type"],data["Rating"],marker="*",color="Pink");

plt.figure(figsize=(10,12))
plt.title("Visualization of Animation")
sns.boxplot(data=data);

sns.boxplot(data["Episodes"]);

sns.distplot(data["Rating"]);
print("Mean Value : ",data["Episodes"].mean())
print("Median Value : ",data["Episodes"].median())

Here the data is not normally distributed it contains left skew

data["Release_season"].value_counts()

sns.barplot(data["Release_season"],data["Episodes"]);

data["Release_year"].value_counts()

sns.distplot(data["Release_year"]);
