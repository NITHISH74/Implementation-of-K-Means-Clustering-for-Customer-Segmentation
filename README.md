# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Moodle-Code Runner

## Algorithm
## Step 1:
Import the necessary packages.
## Step 2:

Read the given csv file and display the few contents of the data.
## Step 3:

Import KMeans and use for loop to calculate the within cluster sum of squares the data.
## Step 4:

Plot the wcss for each iteration, also known as the elbow method plot.
## Step 5:

Predict the clusters and plot them.

## Program:
```python
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: NITHISHWAR S
RegisterNumber:  212221230071

#import packages
import pandas as pd
import matplotlib.pyplot as plt
df=pd.read_csv("Mall_Customers.csv")
df.head()

#checking the data information and null presence
df.info()
df.isnull().sum()

#calculating within cluster sum of squares for each culster and passing it to an array
from sklearn.cluster import KMeans
wcss = []  
for i in range(1,11):
    kmeans = KMeans(n_clusters = i,init = "k-means++")
    kmeans.fit(df.iloc[:,3:])
    wcss.append(kmeans.inertia_)

# visualizing the trend in wcss-elbow method
plt.plot(range(1,11),wcss)
plt.xlabel("No. of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")
plt.show()

#predicting clusters
km = KMeans(n_clusters = 5)
km.fit(df.iloc[:,3:])
y_pred = km.predict(df.iloc[:,3:])
df["cluster"] = y_pred
df0 = df[df["cluster"]==0]
df1 = df[df["cluster"]==1]
df2 = df[df["cluster"]==2]
df3 = df[df["cluster"]==3]
df4 = df[df["cluster"]==4]

#visualising the clusters
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="yellow",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="pink",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="cyan",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="skyblue",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="violet",label="cluster4")
plt.legend()
plt.title("Customer Segments")
plt.show()
*/
```

## Output:
## Initial Dataset:
![image](https://user-images.githubusercontent.com/94164665/173246772-40065882-029a-4706-8172-a614cf32d1bb.png)

## Dataset information:
![image](https://user-images.githubusercontent.com/94164665/173246784-32f9b6e5-383a-4970-9659-b0df8489fe11.png)
![image](https://user-images.githubusercontent.com/94164665/173246790-79432ae8-e29e-47eb-a6a3-c6a3f09f1321.png)

## Elbow method graph (wcss vs each iteration):
![image](https://user-images.githubusercontent.com/94164665/173246799-fb50cbd4-9695-47b4-a6d6-e05ab563cfa6.png)

## Cluster represnting customer segments-graph:
![image](https://user-images.githubusercontent.com/94164665/173246862-959700e1-88f3-40c4-8b0c-c2821dc1afaa.png)


## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
