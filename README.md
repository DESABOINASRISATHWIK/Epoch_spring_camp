# Task-1: Implementation of K-means clustering
## Dataset Loading

The dataset `clustering_data.csv` is loaded using Pandas. Initial exploration includes checking the structure, data types, and any missing values using `df.info()`, followed by previewing the first few records with `df.head()`. This step ensures that the dataset is correctly imported and helps identify necessary preprocessing steps such as handling missing data or converting data types.


## Telangana Pincodes on World Map

This visualization displays the geographic locations of Telangana's pincodes plotted on a world map using **Plotly**. Each point corresponds to a valid latitude and longitude entry from the dataset. The `natural earth` projection provides a global perspective while focusing on India. This plot helps visually confirm the spatial distribution of pincode data and ensures that the data cleaning steps (e.g., converting coordinates to numeric values and removing missing entries) were successful. Such geographic plotting forms the foundation for further spatial analysis or clustering.


## K-means Clustering from Scratch

The following implementation defines the K-means clustering algorithm **without using any external clustering libraries** (like scikit-learn). The algorithm follows the classical K-means steps:

1. **Euclidean Distance Calculation**: Measures the straight-line distance between two points in 2D space (latitude and longitude).
2. **Centroid Initialization**: Randomly selects `k` initial centroids from the dataset.
3. **Cluster Assignment**: Each point is assigned to the nearest centroid based on Euclidean distance.
4. **Centroid Update**: For each cluster, the centroid is recalculated as the mean of all points assigned to it.
5. **Convergence Check**: Iteration continues until centroids do not change significantly (`np.allclose`) or until a maximum number of iterations is reached.

This custom function `kmeans(data, k)` returns both the final centroids and the cluster assignments, allowing full control and transparency over the clustering logic.


## K-means Clustering Visualization (k=5)

The plot below represents the K-means clustering output for Telangana pincode data with **k=5** clusters. Each point represents a pincode location, colored according to the cluster it belongs to. The black **'X' markers** indicate the centroids of each cluster, calculated by averaging the geographic coordinates (latitude and longitude) of the points within each group. This interactive world map, built using Plotly, helps visualize the spatial distribution of pincode clusters across the state, highlighting urban concentrations, semi-urban spreads, and rural dispersions. Such visualization supports geographic analysis and decision-making in planning, logistics, and development.


## Inference and Insights

After applying K-means clustering to the Telangana pincode data, we observed distinct geographical groupings that reveal meaningful patterns across the state.

### Geographical Distribution:
- **Urban Cluster**: A densely packed cluster is observed around Hyderabad, representing the urban core with high pincode density. This includes major areas like Secunderabad and Cyberabad, indicating well-developed infrastructure and population concentration.

- **Semi-Urban Spread**: Surrounding the urban center is a moderately dense cluster covering semi-urban regions such as Ranga Reddy and Medchal-Malkajgiri districts. These areas reflect ongoing urban sprawl and development activity.

- **Rural Distribution**: A more scattered cluster extends into the peripheral regions of Telangana, likely including districts like Mahbubnagar, Vikarabad, or Nalgonda. These points suggest lower population density and a more rural landscape.



### Density and Spread:
- One cluster had a **higher density** of pincodes, representing regions with more developed infrastructure and higher population density.
- Other clusters had **fewer, more spread out** pincodes, which are likely to be in **less populated or remote areas**.

### Potential Implications:
- **Logistics & Delivery**: Companies can treat clusters as service zones for **route optimization and cost reduction**.
- **Business Planning**: Retailers or service providers can use the clusters to **identify demand centers** or underserved regions.
- **Government Planning**: The state can use this clustering for **targeted infrastructure development** (e.g., healthcare, education, transport).

### Conclusion:
The clustering effectively captures the **urban-rural divide** and provides a spatial view of how pincodes are distributed across Telangana. These insights are valuable for planning, decision-making, and strategic deployment of resources.
