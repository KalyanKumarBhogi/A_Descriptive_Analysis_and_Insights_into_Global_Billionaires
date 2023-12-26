The number of billionaires in a country says a lot about the business environment, startup success rate, and many other economic features of a Country. In this project I am going to find the relationship among billionaires around the world.<p>

# Billionaires Analysis with Python <p>

The dataset that I am using to analyze the data about billionaires around the world was curated by Forbes and is downloaded from Kaggle. The dataset contains information about global billionaires in 2021, including their: <p>
1.Names  <p>
2.Net Worth  <p>
3.Country  <p>
4.Source  <p>
5.Rank <p>
6.Age <p>
7.Industry <p>
So let’s get started with the task of billionaires analysis by importing the necessary Python libraries and the dataset: <p>

import pandas as pd <p>
import numpy as np  <p>
import seaborn as sns <p>
import matplotlib.pyplot as plt <p>

data = pd.read_csv("Billionaire.csv") <p>
print(data.head()) <p>

let’s see whether or not this dataset contains missing values: <p>

print(data.isnull().sum()) <p>

So this dataset has 79 missing values in the Age column, let’s remove these rows: <p>
data = data.dropna() <p>

The NetWorth column in this dataset has a $ sign at the beginning of Billionaires’ Net worth and B at the end. So we need to remove these signs and convert the NetWorth column to float: <p>

data["NetWorth"] = data["NetWorth"].str.strip("$")  <p>
data["NetWorth"] = data["NetWorth"].str.strip("B")  <p>
data["NetWorth"] = data["NetWorth"].astype(float)   <p>

Now let’s have a look at the top 10 billionaires according to their NetWorth:  <p>


df = data.sort_values(by = ["NetWorth"], ascending=False).head(10) <p>
plt.figure(figsize=(20, 10)) <p>
sns.histplot(x="Name", hue="NetWorth", data=df) <p>
plt.show() <p>

Now let’s have a look at the top 10 billionaires according to their NetWorth:   <p>


df = data.sort_values(by = ["NetWorth"], ascending=False).head(10) <p>
plt.figure(figsize=(20, 10)) <p>
sns.histplot(x="Name", hue="NetWorth", data=df) <p>
plt.show() <p>

Now let’s have a look at the top 5 domains with the most number of billionaires:  <p>


a = data["Source"].value_counts().head() <p>
index = a.index <p>
sources = a.values v
custom_colors = ["skyblue", "yellowgreen", 'tomato', "blue", "red"] <p>
plt.figure(figsize=(5, 5)) <p>
plt.pie(sources, labels=index, colors=custom_colors) <p>
central_circle = plt.Circle((0, 0), 0.5, color='white') <p>
fig = plt.gcf() <p>
fig.gca().add_artist(central_circle) <p>
plt.rc('font', size=12) <p>
plt.title("Top 5 Domains to Become a Billionaire", fontsize=20) <p>
plt.show() v 


Now let’s have a look at the top 5 industries with the most number of billionaires:   <p>


a = data["Industry"].value_counts().head() <p>
index = a.index <p>
industries = a.values <p>
custom_colors = ["skyblue", "yellowgreen", 'tomato', "blue", "red"] <p>
plt.figure(figsize=(5, 5)) <p>
plt.pie(industries, labels=index, colors=custom_colors) <p>
central_circle = plt.Circle((0, 0), 0.5, color='white') <p>
fig = plt.gcf() <p>
fig.gca().add_artist(central_circle) <p>
plt.rc('font', size=12) <p>
plt.title("Top 5 Industries with Most Number of Billionaires", fontsize=20) <p>
plt.show() <p>

Now let’s have a look at the top 5 countries with the most number of billionaires:   <p>

a = data["Country"].value_counts().head() <p>
index = a.index <p>
Countries = a.values <p>
custom_colors = ["skyblue", "yellowgreen", 'tomato', "blue", "red"] <p>
plt.figure(figsize=(5, 5)) <p>
plt.pie(Countries, labels=index, colors=custom_colors) <p>
central_circle = plt.Circle((0, 0), 0.5, color='white') <p>
fig = plt.gcf() <p>
fig.gca().add_artist(central_circle) <p>
plt.rc('font', size=12) <p>
plt.title("Top 5 Countries with Most Number of Billionaires", fontsize=20) <p>
plt.show()  <p>

The visualization above shows that the United States and China are the countries from which most people become billionaires. So that means the business environment and the startup success rate is really good in the US and China compared to the rest of the world. <p>

# Summary <p>
The success of a business or startup depends a lot on the business environment of a country. At the end of the analysis of global billionaires, I found that China and the United States are the countries with the most billionaires which concludes that the business environment and the success rate of a startup is much better in the US and China than in the rest of the world. <p>

 
