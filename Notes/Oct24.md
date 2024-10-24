# K Nearest Neighbor

- We plot a new point in the dimensions based on its features.
- Then we can see which points from the training data are close to it and predict the class based on that.
- Too small of a `k` value can give too much weight to outliers
- Too big of a `k` value can lead to just classifying everything as the majority class

## Measuring distance

- We could use Euclidean distance for things that are vectors
- We need other types of distance for things that aren't just vectors
    - For nominal attributes, we can use a distance of 1/0 (either same class or not)
- The distance we use affects the decision boundaries we find
    - Manhattan and Euclidean give way different values
    - Euclidean: $d(p,q) = \sqrt{\sum_{i=0}^{n}{(p_i - q_i)^2}}$
    - Manhattan: $d(p,q) = \sum_{i=0}^{n}{(p_i - q_i)}$

## Weighting distance

- We can weight each distance to make closer things have more effect on the classification decision
    - We can use the inverse of distance squared (the closer, the bigger the weight)
        - $w_i = \frac{1}{dist(x_q, x_i)^2}$
            - The $x_q$ is the query point, the one we are trying to classify
        - Gaussian is another weight (close to mean is bigger weight, falls off differently than the one above)

## Challenge question

- Here is the data set

|   X   |   Y   | Label | Distance | Weights |
| :---: | :---: | :---: | :------: | :-----: |
|   1   |   5   |   A   |     2    |   0.25  |
|   0   |   8   |   B   |     4    |  0.063  |
|   9   |   9   |   B   |    10    |   0.01  |
|  10   |  10   |   A   |    12    |  0.007  |

- Here is the new data point: (2,6)
- Do 3-nn with no distance weighting, then with squared inverse distance weighting
- Without weights:
    - 2B and 1A, so B is the class
- With weights:
    - 0.073B and 0.25A, so A is the class

## Regression

- We can just take the mean of the k nearest neighbors
- We can do something similar, but with the weighted distance.
    - We sum up the weighted distance and normalize it with the total value of all weights
    - $f(x_q) = \frac{\sum_{i=1}^{k}{w_i f(x_i)}}{\sum_{i=1}^{k}{w_i}}$



# Dimensionality

- Weird things happen in higher dimensions.
- k-nn isn't great at higher dimensions, because the distances all get very big and they are hard to tell apart from one another
- You can't just have a ton of irrelevant features because they can dominate and override the differences
    - This is the problem with k-nn and many dimensions, even if all are relevant, all are not relevant at the same time
        - We can do something to weight the attributes (like other models do), but k-nn can no longer be a lazy learner

## Reduction techniques

- Ways to slim down the training set to keep the algorithm efficient (not necessarily more accurate)
    - We could only keep the center points of our decision surface
    - We could only keep the border points (this gives good accuracy)
    - We could only keep the point if it would not be classified correctly (so sort of test as you train idea...)

# Value Difference Metric

- We can use this to get the distance between nominal data
- The idea is that if a feature that is nominal has a split in the value and the class the point with that value belongs to, the different values have a large distance
- There is a formula to calculate it:
    - $vdm_a(x,y) = \sum_{c=1}^{C}{(\frac{N_{a,x,c}}{N_{}a,x}-\frac{N_{a,y,c}}{N_{a,y}}})^2$
