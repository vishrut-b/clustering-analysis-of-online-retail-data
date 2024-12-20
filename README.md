## 📊 Online Retail Data Analysis using KMeans Clustering

Welcome to the Online Retail Data Analysis project! This repository showcases data preprocessing, customer segmentation, and clustering using the KMeans algorithm.

### 📁 Project Overview
This project involves analyzing online retail transaction data. The goal is to segment customers based on their purchase behavior using clustering techniques.

### 🚀 Key Features
- **Data Cleaning:** Removal of outliers, missing values, and invalid records.
- **Feature Engineering:** Creation of meaningful features like monetary value, purchase frequency, and recency.
- **Clustering Analysis:** Implementation of KMeans clustering to identify distinct customer groups.

### 🛠️ Tech Stack
- **Languages:** Python
- **Libraries:** Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn

### 📈 Methodology
1. **Exploratory Data Analysis (EDA):** Initial inspection and visualization.
2. **Data Cleaning:** Removing inconsistencies and irrelevant records.
3. **Feature Engineering:** Creating and scaling important features.
4. **Clustering:** Using KMeans with the elbow method and silhouette score.
5. **Results Interpretation:** Defining customer segments and recommending targeted strategies.

### 📊 Key Code Snippets
#### KMeans Clustering Implementation
```python
from sklearn.cluster import KMeans
from sklearn.metrics import silhouette_score

# Determine optimal number of clusters
max_k = 12
inertia = []
silhouette_scores = []

for k in range(2, max_k + 1):
    kmeans = KMeans(n_clusters=k, random_state=42, max_iter=1000)
    cluster_labels = kmeans.fit_predict(scaled_data_df)
    inertia.append(kmeans.inertia_)
    silhouette_scores.append(silhouette_score(scaled_data_df, cluster_labels))
```

#### Fitting the Model
```python
# Applying KMeans with optimal clusters
kmeans = KMeans(n_clusters=4, random_state=42, max_iter=1000)
cluster_labels = kmeans.fit_predict(scaled_data_df)
primary_df['cluster'] = cluster_labels
```

### 📊 Results
The following customer clusters were identified:
- **Cluster 0 - "Fidéliser":** High-value, frequent customers.
- **Cluster 1 - "Réengager":** Infrequent, low-value customers.
- **Cluster 2 - "Nourrir":** New or low-activity customers.
- **Cluster 3 - "Récompenser":** Loyal, high-spending customers.

### 📚 Learnings
- Data preprocessing and feature scaling.
- Effective clustering and model evaluation.
- Customer segmentation using real-world business data.

### 💡 Future Enhancements
- Use advanced clustering methods (e.g., DBSCAN, hierarchical clustering).
- Implement automated data cleaning pipelines.
- Build a dashboard for interactive results visualization.

### 📧 Contact
Feel free to connect via [LinkedIn](www.linkedin.com/in/vishrut-bezbarua-53b355205) or reach out via [email](vishrutbezbarua@gmail.com).

**Thank you for visiting this repository! ⭐ Feel free to fork and contribute!**

