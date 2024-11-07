# Unsupervised learning

- We want to separate our data in anywhere from $2$ to $n - 1$ classes
- We want there to be similarity in a class and disimilarity between the classes
- There are many ways to separate the data into classes and we want to find some way to do so meaningfully

## Clustering

- How do we decide how to cluster?
    - One way is Euclidean distance
    - We can find other ways to measure and cluster by similarity
    - We want the features to be normalized so that nothing dominates the rest

### How to handle outliers

- We can change the number of clusters (k) to find
- We can remove clusters with few data points
- We can find ways to remove or ignore the outliers before we train the model

### Distance between clusters

- We can measure with the centroid (a mean in the middle representing all other points), getting the distance between cluster centroids
- We can measure the medoid (an actual point in the cluster from which all other points are least distant)
- We can get the smallest distance between points in the 2 clusters (</b>Single Link</b>)
- we can get the largest distance between points in the 2 clusters (</b>Complete Link</b>)

### Hierarchical Clustering

- Every points is its own cluster
- We take the two closest clusters and merge them
- Then we take the next two... until we have the right amount of clusters
- Or we can go the other way, making all points in one cluster and dividing into smaller clusters

#### Hierarchical Agglomerative Clustering (HAC)

- Input is $n$ x $n$ adjacency matrix
- start each point in its own cluster
- Repeat until there is just one cluster containing all points
- Choose which clustering you want 
- This varies by the definition of closeness you use (average [centroid], single, complete)

### Ward Linkage

- We look at the variance for each cluster.
- The distance is a measure of how much the sum squared difference changes (increases) when we combine two clusters
- We, as always, choose the minimum increase first

# Cluster Metrics

- We need a way to tell how many clusters we want
- We can do this by looking at cluster metrics
    - We want clusters that are far apart, but that are themselves closely clumped
    - We can find a way to measure these things
- Then, when we have clusters (from whatever method we want) and we measure the metrics to see how good of clusters we have. This lets us test a lot of cluster types (lots of k for example) and find the best of them.

## Silhouette

- This finds a balance between inter-cluster similarity and intra-cluster dissimilarity
- $a(i)$ - the average distance between you and all other points in your cluster
- $b(i)$ - the average distance between you and all other points in the next closest cluster
- $s(i)$ - the final score
    - $s(i) = \frac{b(i) - a(i)}{max(a(i), b(i))}$
    - Your $b(i)$ should be the bigger
    - $-1 \ge s(i) \le 1$
    - If you get a negative score, you probably should have been in that next closest class
- We can get the $s(i)$ score for a whole cluster by averaging the $s(i)$ for each instance
- WE can do the same for the whole clustering the same way
- We want those two things to be big (that means the instances are in their right clusters)
