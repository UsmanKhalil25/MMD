## Question 1

### Clustering Insights Report

**1. Elbow Method Findings:**  
- The elbow plot indicated that **K = 5 or 6** offers the best trade-off between reducing within-cluster error and avoiding overfitting.  
- This optimal range was then used for the bisecting K-means implementation.

**2. Method Comparisons:**

- **Bisecting K-means (K=5):**  
  - **SSE:** ~1.19e+14  
  - **Time:** ~0.034 s  
  - **Insight:** Provides efficient clustering with competitive error levels and fast computation, making it suitable for large datasets.

- **Hierarchical Clustering:**  
  - **Single Linkage:**  
    - **SSE:** ~3.37e+14  
    - **Time:** ~0.227 s  
    - **Observation:** Higher SSE likely due to chaining effects.
  - **Complete Linkage:**  
    - **SSE:** ~1.05e+14  
    - **Time:** ~1.005 s  
    - **Observation:** Achieves low SSE (tighter clusters) but is computationally more expensive.
  - **Average Linkage:**  
    - **SSE:** ~1.16e+14  
    - **Time:** ~0.780 s  
    - **Observation:** Balances between single and complete linkage performance.

- **DBSCAN:**  
  - **SSE:** Not applicable (nan)  
  - **Time:** ~0.039 s  
  - **Insight:** As a density-based method, DBSCAN does not optimize centroid-based error. It excels in detecting arbitrary shapes and outliers rather than minimizing SSE.

**3. Overall Insights:**  
- **Optimal Clustering:** The elbow method supports using K=5/6, and the bisecting K-means method effectively leverages this to provide fast and efficient clustering.  
- **Method Trade-offs:**  
  - **Bisecting K-means** offers a good balance of speed and quality.  
  - **Hierarchical methods** (especially complete linkage) can yield lower errors but at higher computational costs.  
  - **DBSCAN** is useful for datasets with noise or non-spherical clusters, even though traditional SSE is not its performance metric.

## Question 2

The results indicate:

- **K-Means:**  
  - Runs show some variability (WCSS ranging from ~19.1 to ~22.1), which reflects sensitivity to initialization.  
  - Convergence is very fast (2–6 iterations) and computation time is minimal (~0.002–0.004 sec).  
  - The between-cluster sum (BCSS) remains relatively high, suggesting well-separated clusters.

- **Hierarchical Clustering:**  
  - For all three linkage methods, SSE decreases as K increases (expected behavior).  
  - Single and average linkage give similar SSEs, while complete linkage starts higher for K=2 but becomes lower for K=3 and K=4, indicating that the choice of linkage can greatly affect cluster compactness.  
  - All methods run extremely fast (around 0.001–0.003 sec).

**Overall Comparison:**  
- **Quality:** K-Means shows lower WCSS values in some runs, suggesting tighter clusters, but its performance depends on initialization. Hierarchical methods vary by linkage, with complete linkage yielding better SSE at higher K values in this case.
- **Time:** Both methods are computationally efficient for this dataset.
- **Consistency:** Hierarchical clustering is deterministic, while K-Means varies across runs.

In summary, K-Means produces compact clusters quickly but can be sensitive to initialization, while hierarchical clustering (depending on the linkage method) can provide comparable quality with the added benefit of a dendrogram to visualize the cluster hierarchy.