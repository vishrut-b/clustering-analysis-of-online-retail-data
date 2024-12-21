---
layout: default
title: "Customer Segmentation with KMeans Clustering"
description: "A short description of your project"
---

# Customer Segmentation Project Using K-Means Clustering

## Table of Contents
1. [Overview](#overview)
2. [Dataset Description](#dataset-description)
3. [Objective](#objective)
4. [Theoretical Background](#theoretical-background)
    - [Why K-Means Clustering?](#why-k-means-clustering)
    - [Understanding the Algorithm](#understanding-the-algorithm)
5. [Methodology](#methodology)
    - [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
    - [Data Cleaning](#data-cleaning)
    - [Feature Engineering](#feature-engineering)
    - [Data Scaling and Preprocessing](#data-scaling-and-preprocessing)
    - [Clustering Process](#clustering-process)
6. [Key Results](#key-results)
7. [Customer Segmentation Strategies](#customer-segmentation-strategies)
8. [Conclusion](#conclusion)
9. [References](#references)

---

## Overview
This project utilizes K-Means clustering, an unsupervised machine learning algorithm, to segment customers based on their purchasing behavior. By understanding customer profiles, businesses can tailor their strategies to boost customer satisfaction, loyalty, and revenue.

## Dataset Description
The dataset contains transaction records for an online retailer based in the UK, spanning two business years.

| **Feature**   | **Description**                                                                 |
|---------------|---------------------------------------------------------------------------------|
| `InvoiceNo`   | Unique 6-digit identifier for each transaction. Cancellation codes start with 'C'. |
| `StockCode`   | Unique code assigned to each product.                                           |
| `Description` | Name of the product.                                                            |
| `Quantity`    | Number of units purchased in a transaction.                                     |
| `InvoiceDate` | Date and time of the transaction.                                               |
| `UnitPrice`   | Price per unit in GBP (£).                                                      |
| `CustomerID`  | Unique identifier for each customer.                                            |
| `Country`     | Country where the customer resides.                                             |

---

## Objective
The primary goals of this project are:
- To identify meaningful customer groups based on purchasing behavior.
- To understand the characteristics of each customer segment.
- To provide actionable insights for improving marketing and customer engagement strategies.

---

## Theoretical Background

### Why K-Means Clustering?
K-Means is chosen for this project because:
1. **Efficiency**: K-Means works well with large datasets and provides quick clustering results.
2. **Scalability**: It can handle a variety of data sizes and complexities.
3. **Interpretability**: The results are easy to visualize and interpret, especially for customer segmentation tasks.
4. **Versatility**: It works well with numerical data, which is predominant in this dataset.

### Understanding the Algorithm

#### Steps in K-Means Clustering:
1. **Initialization**:
   - Choose the number of clusters (‘k’).
   - Randomly initialize cluster centroids.
2. **Assignment Step**:
   - Assign each data point to the nearest centroid using the Euclidean distance.
3. **Update Step**:
   - Recalculate the centroids by taking the mean of all points assigned to a cluster.
4. **Convergence**:
   - Repeat steps 2 and 3 until the centroids no longer change significantly or a predefined number of iterations is reached.

#### Mathematical Objective:
K-Means minimizes the **Within-Cluster Sum of Squares (WCSS)**:

{% raw %}
$$WCSS = \sum_{i=1}^{k} \sum_{x \in C_i} \| x - \mu_i \|^2$$
{% raw %}

Where:
- k: Number of clusters  
- $C_{i}$: Cluster \( i \)  
- $\mu_{i}$: Centroid of cluster \( i \)  
- x: Data point  

#### Silhouette Score:
The **Silhouette Score** evaluates the quality of clustering by comparing intra-cluster and inter-cluster distances. It ranges from \(-1\) to \(1\):

$$
S(i) = \frac{b(i) - a(i)}{\max\{a(i), b(i)\}}
$$

Where:
- \( a(i) \): Average distance between \( i \) and other points in the same cluster.  
- \( b(i) \): Average distance between \( i \) and points in the nearest cluster.  

---

## Methodology

### Exploratory Data Analysis (EDA)
EDA involved:
1. Checking for null values and invalid data (e.g., negative prices).
2. Analyzing the distribution of numerical features like `Quantity`, `UnitPrice`, and `CustomerID`.
3. Identifying patterns in `InvoiceDate` and `Country` to uncover insights into purchasing trends.

#### Observations:
- A significant number of transactions had missing `CustomerID` values.
- Negative or zero values in `Quantity` and `UnitPrice` indicated potential errors or special promotions.

### Data Cleaning
1. **Removing Invalid Entries**:
   - Dropped rows with missing `CustomerID`.
   - Excluded transactions with negative or zero `Quantity` and `UnitPrice`.
2. **Processing Categorical Variables**:
   - Cleaned `StockCode` by removing non-product entries like "ADJUST" and "TEST".

### Feature Engineering
1. **Created New Features**:
   - `sales_line_total = Quantity × UnitPrice`: Total revenue per transaction.
2. **Aggregated Data**:
   - Grouped by `CustomerID` to calculate:
     - **Monetary Value**: Total spending.
     - **Frequency**: Number of unique transactions.
     - **Recency**: Days since the last purchase.

### Data Scaling and Preprocessing
- Used **StandardScaler** to normalize features (`Monetary Value`, `Frequency`, `Recency`) with Z-score scaling:
  
  $$
  Z = \frac{X - \mu}{\sigma}
  $$

### Clustering Process
1. **Optimal K Selection**:
   - Used the **Elbow Method** and **Silhouette Scores** to determine \( k = 4 \).
2. **K-Means Execution**:
   - Clustered scaled data into four segments.

---

## Key Results

### Cluster Analysis

| **Cluster** | **Characteristics**                       | **Description**                                                      |
|-------------|-------------------------------------------|----------------------------------------------------------------------|
| `0`       | High-value, frequent buyers               | Regular buyers with high spending.                                   |
| `1`       | Infrequent, low-value customers           | Customers who purchase sporadically.                                 |
| `2`       | New or low-engagement customers           | Customers with low spending but recent activity.                     |
| `3`       | Loyal, high-frequency, high-value buyers  | The most valuable customers in terms of revenue and engagement.      |

---

## Customer Segmentation Strategies

### Cluster 0: "Retain"
- **Rationale**: High-value customers who make frequent purchases.
- **Actions**:
  - Introduce loyalty programs.
  - Provide personalized recommendations.

### Cluster 1: "Re-Engage"
- **Rationale**: Customers with sporadic and low spending patterns.
- **Actions**:
  - Send targeted email campaigns.
  - Offer exclusive discounts to incentivize purchases.

### Cluster 2: "Nurture"
- **Rationale**: Recent customers with potential for growth.
- **Actions**:
  - Offer onboarding incentives.
  - Provide exceptional customer service.

### Cluster 3: "Reward"
- **Rationale**: Top-performing customers in terms of revenue and frequency.
- **Actions**:
  - Develop a premium rewards program.
  - Provide exclusive early access to products or events.

---

## Conclusion
K-Means clustering successfully segmented customers into actionable groups. These insights can drive personalized marketing and improve overall business strategy.

### Next Steps
1. Deploy the clustering model in a production environment.
2. Integrate segmentation results into CRM systems.
3. Experiment with alternative clustering algorithms (e.g., Hierarchical Clustering).

---

## References
- [Scikit-learn Documentation](https://scikit-learn.org/)
- [K-Means Clustering Guide](https://en.wikipedia.org/wiki/K-means_clustering)
