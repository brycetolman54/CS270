# More on Features

- <i>Feature Selection</i>: This is when you reduce the number <i>n</i> of features that you have by selecting only some to work with
- <i>Feature Reduction</i>: This is when you reduce the number of your features by combining them, hopefully retaining all the info

## Feature Selection

- We can use filters and wrappers

### Filters

- These are independent of any specific algorithm
- You can do something like looking at the correlation of each feature with the outcome of the model
    - This says that good features have high correlation
    - The problem is that when you have a feature with low first-order correlation, you get rid of it (when it could have high higher-order correlation)
- You could also score subsets of features together rather than individually
- You could use a decision tree algorithm to train a couple of trees, see which features those ignore, and use those features in a better model

### Wrappers

- This is what he suggests we use
- This optimizes for a specific algorithm
- The idea is to choose some feature subsets, a limited amount. We pass that to the algorithm, see how well it does on the validation set, then use the best.
    - We can't test all of the subsets, so we can use a greedy algorithm
- Here are some examples of the Greedy algorithms:
    - <b>Forward Search</b>: complexity is $O(n^2 * learning\ or\ test\ time)$
        1. Score each feature by itself and add the best to your feature set (FS)
        2. Test each subset of the feature with all others features, choose the best outcome to add that feature to the FS
        3. Keep adding features like this until you don't get better results upon adding a new feature
        - There is a problem here, where you could stop early since you could never combine features that work really well together but not well apart
    - <b>Backward Search</b>: complexity is $O(n^2 * learning\ or\ test\ time)$
        1. Score the initial feature set with all features (FS)
        2. Test each subset with all features but removing one and get rid of the feature that causes the least decrease in accuracy
        3. Keep going until dropping any feature causes a significant decrease in accuracy
    - <b>Principal Component Analysis</b> (PCA):
        - You have your data in your original basis set. 
        - You want to find a new basis set that contains you data, but where the <i>first component</i> is the dimension along which there is the most variance
        - The second, third and so on are the next most variant dimensions
        - You can find the <i>n</i> principal components for your <i>n</i> dimensions, then drop the components that have the least variance
        - The downside is that <i>PCA</i> works for linear data, not so much otherwise

#### Variance and Covariance

- The variance is how much data is spread in one feature/dimension
- The covariance is how two dimensions vary from one another
    - If the two features have 0 covariance, we should keep both
    - If the two features have high covariance, we can get rid of one of them (or combine them somehow)

#### How to do PCA

- We need to make the mean 0 for all data points
    - Take the mean value of the dimension, subtract that from each data point
    - This makes the mean in the covariance equation easy to deal with
- We make a matrix where the diagonal is the variance of each feature and the off diagonal are the covariance of the features
- Once we have that matrix, we calculate the eigenvectors and eigenvalues of that matrix
    - The eigenvectors are the new basis set for the data
    - The eigenvalue corresponds to the variance along each new dimension (great, this is what we wanted to know which to drop)
- We keep only <i>p</i> of the original <i>n</i> features. Then we can calculate the <b>proportion of variance</b> to see how that varies
    - $\frac{\sum_{i=1}^{p}\lambda_i}{\sum_{i=1}^{n}\lambda_i}$
    - λ here is the eigenvalue of each feature


# Exam Things

- 
