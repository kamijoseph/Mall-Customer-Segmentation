# Customer Segmentation for Targeted Marketing

## Introduction
This project tackles a fundamental business problem: understanding customer base composition. By segmenting customers into distinct groups based on purchasing behavior and demographics, a company can execute targeted marketing campaigns, improve customer service, and optimize product offerings. This analysis uses unsupervised machine learning to discover these hidden patterns.

## Data Overview
The Mall Customer Segmentation Data contains 200 records with the following features:
- `CustomerID`: Unique identifier (was dropped for analysis).
- `Gender`: Categorical variable (Encoded: Male=0, Female=1).
- `Age`: Customer's age in years.
- `Annual Income (k$)`: Customer's annual income in thousands of dollars.
- `Spending Score (1-100)`: A score assigned by the mall based on customer behavior and spending nature.

|   | Gender | Age | Annual Income (k$) | Spending Score (1-100) |
|---|--------|-----|-------------------|------------------------|
| 0 | 1      | 19  | 15                | 39                     |
| 1 | 1      | 21  | 15                | 81                     |
| 2 | 0      | 20  | 16                | 6                      |
| ... | ... | ... | ... | ... |

## Methodology
1.  **Data Preprocessing:** Handled missing values (none found), encoded the 'Gender' variable, and scaled all features using StandardScaler.
2.  **Determining Clusters (k):** Used the **Elbow Method** on the K-Means algorithm to find the optimal number of clusters.
3.  **Clustering:** Applied **K-Means** with the optimal `k` to segment the customers.
4.  **Visualization:** Employed **Principal Component Analysis (PCA)** to reduce the dimensionality of the data and visualize the clusters in 2D.
5.  **Validation:** Supported the K-Means result by visually inspecting a **Hierarchical Clustering Dendrogram**.

## Results

### 1. Optimal Number of Clusters (k)
The Elbow Method showed a clear inflection point at `k=4`, indicating that four distinct customer segments exist.
![Elbow Method Plot](wcss.png)

### 2. Cluster Visualization
The following PCA plot shows the four customer segments, visually separated in 2D space.
![PCA Plot](pca_plot.png)

### 3. Customer Segment Profiles
The following table describes the average characteristics of each cluster, allowing us to assign meaningful labels. A key finding is the clear gender-based spending behavior within similar age and income brackets.

| Cluster | N | Gender (Prop. Female) | Age | Annual Income | Spending Score | Label & Description |
|:-------:|:-:|:---------------------:|:---:|:-------------:|:--------------:|:-------------------:|
| **0** | 40 | 0% | 28.3 | 62.0k | 71.7 | **Young Big Spenders (Male):** Young men with solid incomes and a high willingness to spend. Target with marketing for electronics, sports apparel, and luxury goods. |
| **1** | 57 | 100% | 28.4 | 59.7k | 67.7 | **Young Big Spenders (Female):** Young women with solid incomes and a high willingness to spend. Target with marketing for fashion, cosmetics, and lifestyle brands. |
| **2** | 48 | 0% | 49.4 | 62.4k | 29.2 | **Frugal Middle-Aged (Male):** Middle-aged men with good incomes but very low spending. Value-driven and pragmatic. Messaging should focus on durability, utility, and essential items. |
| **3** | 55 | 100% | 48.1 | 58.8k | 34.8 | **Frugal Middle-Aged (Female):** Middle-aged women with good incomes but low spending. Practical and deliberate shoppers. Target with value-based messaging for quality staples and family-oriented products. |

*Table: Interpretation of the four customer clusters based on mean values. The spending divergence between genders in similar age groups is a critical insight.*

## Conclusion & Business Recommendations
Based on the clustering analysis, we recommend the marketing team tailor its strategies to these four distinct segments:

1.  **Target Young Big Spenders (Clusters 0 & 1):** This is the most valuable demographic. Engage them on social media (TikTok, Instagram) with trendy, aspirational, and high-quality products. Campaigns can be gender-specific:
    *   **For Men (Cluster 0):** Focus on technology, fitness, and automotive niches.
    *   **For Women (Cluster 1):** Focus on fashion, beauty, and wellness niches.

2.  **Re-engage Frugal Middle-Aged Customers (Clusters 2 & 3):** The goal here is to increase their spending. They have the income but are not converting it into purchases. Strategies must be tailored:
    *   **For Men (Cluster 2):** Highlight product reliability, longevity, and smart investment. Discounts and bulk deals may be effective.
    *   **For Women (Cluster 3):** Emphasize quality, family value, and multi-purpose products. Trusted reviews and testimonials will be key.

This data-driven approach reveals that gender is a powerful behavioral indicator alongside age and income. Allowing for highly personalized marketing will ultimately increase ROI and customer satisfaction.