# BLENDED LEARNING
# Implementation of Customer Segmentation Using K-Means Clustering

## AIM:
To implement customer segmentation using K-Means clustering on the Mall Customers dataset to group customers based on purchasing habits.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Import pandas, sklearn.cluster.KMeans, sklearn.preprocessing.StandardScaler
2. Load CustomerData.csv: data = pd.read_csv('CustomerData.csv')
3. Display data: print(data.head()); print(data.columns)
4. Select features: features = ['Age','Annual Income (k$)','Spending Score (1-100)']
5. X = data[features]; scaler = StandardScaler(); X_scaled = scaler.fit_transform(X)
6. kmeans = KMeans(n_clusters=4, random_state=42); kmeans.fit(X_scaled)
7. cluster_labels = kmeans.labels_; print("Silhouette Score:", silhouette_score(X_scaled, cluster_labels))
8. data['Cluster'] = cluster_labels
9. Visualize: sns.scatterplot(data=data, x='Annual Income (k$)', y='Spending Score (1-100)', hue='Cluster')
10. plt.title('Customer Segmentation'); plt.show()
 

## Program:
```
/*
Program to implement customer segmentation using K-Means clustering on the Mall Customers dataset.
Developed by: Sanjeev Kumar K
RegisterNumber:  25012334

import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.cluster import KMeans
from sklearn.preprocessing import StandardScaler
from sklearn.metrics import silhouette_score
data=pd.read_csv("CustomerData.csv")
print(data.head())
print(data.columns)
features = ['Age', 'Annual Income (k$)', 'Spending Score (1-100)']
X = data[features]
features = ['Age', 'Annual Income (k$)', 'Spending Score (1-100)']
X = data[features]
scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)
wcss = [] 
for i in range(1, 11):
    kmeans = KMeans(n_clusters=i, random_state=42)
    kmeans.fit(X_scaled)
    wcss.append(kmeans.inertia_)
plt.figure(figsize=(8, 4))
plt.plot(range(1, 11), wcss, marker='o', linestyle='--')
plt.xlabel('Number of Clusters')
plt.ylabel('WCSS')
plt.title('Elbow Method for Optimal Number of Clusters')
plt.show()
optimal_clusters = 4
kmeans = KMeans(n_clusters=optimal_clusters, random_state=42)
kmeans.fit(X_scaled)
data['Cluster'] = kmeans.labels_
sil_score = silhouette_score(X_scaled, kmeans.labels_)
print(f"Silhouette Score: {sil_score}")
plt.figure(figsize=(10, 6))
sns.scatterplot(data=data, x='Annual Income (k$)', y='Spending Score (1-100)', hue='Cluster', palette='viridis', s=100, alpha=0.7)
plt.title('Customer Segmentation based on Annual Income and Spending Score')
plt.xlabel('Annual Income (k$)')
plt.ylabel('Spending Score (1-100)')
plt.legend(title='Cluster')
plt.show()

*/
```

## Output:
![alt text](<Screenshot 2026-03-10 221532.png>)
![alt text](<Screenshot 2026-03-10 221549.png>)

## Result:
Thus, customer segmentation was successfully implemented using K-Means clustering, grouping customers into distinct segments based on their annual income and spending score. 
