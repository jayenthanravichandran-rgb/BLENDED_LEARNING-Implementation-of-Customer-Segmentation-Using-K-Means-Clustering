# BLENDED LEARNING
# Implementation of Customer Segmentation Using K-Means Clustering

## AIM:
To implement customer segmentation using K-Means clustering on the Mall Customers dataset to group customers based on purchasing habits.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
Step 1: Start

Step 2: Import Required Libraries
Import necessary Python libraries:

pandas for data handling
matplotlib.pyplot and seaborn for visualization
KMeans from sklearn.cluster for clustering
StandardScaler for feature scaling
silhouette_score for evaluation

Step 3: Load the Dataset

Read the dataset file CustomerData.csv using pd.read_csv()
Display first few rows using head()
Display column names using columns

Step 4: Select Features

Choose relevant features:
Age
Annual Income (k$)
Spending Score (1-100)
Store them in variable X

Step 5: Data Preprocessing (Scaling)

Initialize StandardScaler()
Fit and transform the data using fit_transform()
Store scaled data in X_scaled

Step 6: Determine Optimal Number of Clusters (Elbow Method)

Initialize empty list wcss
For values of K from 1 to 10:
Apply K-Means clustering
Fit the model on X_scaled
Compute inertia (WCSS) and append to list
Plot graph:
X-axis: Number of clusters
Y-axis: WCSS
Identify optimal K (elbow point)

Step 7: Apply K-Means Clustering

Initialize K-Means with chosen clusters (e.g., K = 5)
Fit model on X_scaled

Step 8: Assign Cluster Labels

Add cluster labels to dataset using kmeans.labels_
Create a new column Cluster in dataset

Step 9: Evaluate Clustering Performance

Calculate Silhouette Score using silhouette_score()
Print the score

Step 10: Visualize Clusters

Create scatter plot using seaborn.scatterplot():
X-axis: Annual Income
Y-axis: Spending Score
Hue: Cluster
Add title, labels, and legend
Display plot

Step 11: Stop

## Program:
```
/*
Program to implement customer segmentation using K-Means clustering on the Mall Customers dataset.
Developed by: R JAYENTHAN
RegisterNumber:  212225240057

import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.cluster import KMeans
from sklearn.preprocessing import StandardScaler
from sklearn.metrics import silhouette_score

data=pd.read_csv('CustomerData.csv')

print(data.head())
print(data.columns)

features = ['Age', 'Annual Income (k$)', 'Spending Score (1-100)']
X = data[features]

scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)

wcss=[]
for i in range(1,11):
    kmeans = KMeans(n_clusters=i,random_state=42)
    kmeans.fit(X_scaled)
    wcss.append(kmeans.inertia_)
    
plt.figure(figsize=(8,4))
plt.plot(range(1,11),wcss,marker='o',linestyle='-')
plt.xlabel("Number of Clusters")
plt.ylabel("WCSS")
plt.title("Elbow Method for Optimal Number of Clusters")
plt.show()


kmeans = KMeans(n_clusters=5, random_state=42)
kmeans.fit(X_scaled)

data['Cluster'] = kmeans.labels_

sil_score = silhouette_score(X_scaled, kmeans.labels_)
print(f'Silhouette Score: {sil_score}')

plt.figure(figsize=(10, 6))
sns.scatterplot(data=data, x='Annual Income (k$)', y='Spending Score (1-100)', hue='Cluster', palette='viridis')
plt.title('Customer Segmentation based on Annual Income and Spending Score')
plt.xlabel('Annual Income (k$)')
plt.ylabel('Spending Score (1-100)')
plt.legend(title='Cluster')
plt.show()
*/
```

## Output:
  <img width="668" height="157" alt="image" src="https://github.com/user-attachments/assets/92397455-6fd3-4508-956e-85972c063385" />
  <img width="835" height="393" alt="image" src="https://github.com/user-attachments/assets/7f902461-5e6d-4855-ad73-00433d72d15c" />
  <img width="963" height="581" alt="image" src="https://github.com/user-attachments/assets/233a2e1c-501a-4f18-b969-8fa69ac8b849" />



## Result:
Thus, customer segmentation was successfully implemented using K-Means clustering, grouping customers into distinct segments based on their annual income and spending score. 
