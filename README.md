# MSCS 634 - Lab 5: Clustering with Hierarchical and DBSCAN Techniques

👨‍💻 Student Name  
Chandra Kiran Billingi

📚 Course  
MSCS 634 - Advanced Big Data and Data Mining

🧪 Lab Overview  
In this lab, I explored unsupervised learning techniques using clustering algorithms on the Wine dataset from `sklearn.datasets`. The goal was to apply and evaluate both **Hierarchical Clustering** and **DBSCAN**, analyze their clustering performance, and compare their effectiveness under different settings.

I have implemented:

- **Hierarchical Clustering** (Agglomerative with different numbers of clusters)
- **DBSCAN Clustering** (with and without PCA-based dimensionality reduction)

Clustering performance was evaluated using:

- **Silhouette Score** – to measure cluster cohesion and separation  
- **Homogeneity Score** – to measure if each cluster contains only members of a single class  
- **Completeness Score** – to check if all members of a given class are assigned to the same cluster

---

🧾 Step-by-Step Breakdown

📌 **Step 1: Data Preparation**  
- Loaded the Wine dataset using `load_wine()` from `sklearn.datasets`.  
- Converted the data into a pandas DataFrame and added the target column.  
- Scaled all features using `StandardScaler` for effective distance-based clustering.

📌 **Step 2: Hierarchical Clustering**  
- Applied **Agglomerative Clustering** using scikit-learn.  
- Tried multiple `n_clusters` values (2, 3, 4) and plotted cluster visualizations.  
- Found that `n_clusters = 3` aligned best with the wine classes.  
- Silhouette and homogeneity scores were moderately good.

📌 **Step 3: DBSCAN Clustering (initial attempt)**  
- Applied DBSCAN on the full-dimensional scaled dataset.  
- Tried various `eps` and `min_samples` values, but all results labeled **all data points as noise (-1)**.  
- Concluded DBSCAN struggled in high-dimensional feature space.

📌 **Step 4: DBSCAN Clustering with PCA**  
- Reduced data to **2 principal components** using PCA.  
- Re-applied DBSCAN with tuned parameters (`eps=0.5`, `min_samples=5`) on the PCA-transformed data.  
- Successfully formed ≥2 clusters and computed **Silhouette**, **Homogeneity**, and **Completeness** scores.  
- Some points were marked as noise, highlighting DBSCAN's ability to detect outliers.

---

💡 **Key Insights**
- Hierarchical clustering is intuitive and works well when the number of clusters is known.
- DBSCAN failed in full dimensions but performed well with PCA-reduced data.
- DBSCAN’s strength lies in detecting arbitrarily shaped clusters and noise points.
- PCA is crucial for improving DBSCAN performance on high-dimensional datasets.
- Parameter tuning (especially `eps` in DBSCAN) significantly affects clustering outcome.

---

🛠️ **Challenges & Troubleshooting**
- ❌ DBSCAN labeled all points as noise in original space → required dimensionality reduction.  
- ✅ Implemented **PCA** to reduce dimensionality → improved DBSCAN performance.  
- ⚠️ Silhouette Score was not computable until DBSCAN formed ≥2 clusters.  
- 📊 Had to manually try different `eps` values to find a working configuration.

---


