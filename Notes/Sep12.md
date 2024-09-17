# Why do we need a bias?

- The program is trying to find a plane that separates our data points
- If we have no bias, the plane must always go through the origin
- The bias allows us to move the plane around

# Linear Separability

- Simple data can be linearly separable
- If there are data that are not linearly separable, we have to ask if they are exceptions to our rules or just noise
- In order to fix these cases where things are not linearly separable we can use a multilayer perceptron

- What if we need more than yes or no?
    - We could make a perceptron for each category we want to recognize and train each one on to see their category as 1 and all else as 0
        - If two perceptrons both give a 1 for the same set of data, we look at the net and see which is higher (which is more confident)

# Objective Functions

- How do we judge the quality of a particular model?
    - Classification accuracy and error: #correct/Total and #incorrect/Total
    - Pattern error: sum of absolute value differences between the target and output of each (this is L1 loss)
    - Sum squared error: sum of square difference between the target and output of each (accentuates the outliers), this is L2 loss
    - Sum squared error (SSE): sum of a sum of the squares of the difference between the target and output
    - Mean squared error: take SSE for all data in the dataset, then average those returns
    - Root mean squared error: take MSE of the list of mean squared error and take the square root of it


|   x   |   y   | Output | Target | Data Set |
| :---: | :---: | :----: | :----: | :------: |
|   2   |  -3   |  1     |   1    |          |
|   0   |  1    |   0    |   1    |          |
|  0.5  | 0.6   |  0.8   |  0.2   |          |
|  L1   |       |        |        |    1.6   |
|  SSE  |       |        |        |   1.36   |
|  MSE  |       |        |        |  0.456   |
| RMSE  |       |        |        |  0.642   |

# Gradient Descent Learning

- We are trying to maximize or minimize the objective function
- We can look at the SSE versus the weight values, our function looks around this landscape to find the minimum of the graph (not global, but a good one)
- We take the partial derivative with respect to each of the weights, we want to find a formula for this that finds a negative value so we head to a minimum
    - We use the δ rule: `Δw_i = c(t - net)x_i`
    - The difference is the ``t - net` instead of `t - z`
    - This guarantees that we will have a parabolic surface, so we hit the minimum

# Linearly Separable Boolean Functions

- d = # of dimensions
- P = 2<sup>d</sup> = # of patterns
- 2<sup>2<sup>d</sup></sup> = # of functions
- This grows fast, the perceptron can only solve linearly separable functions of small numbers of variables (very few real problems are linearly separable)
- While the perceptron can't handle that, we can handle it in a perceptron-like way
    - We combine the inputs in funky ways to give new inputs to the perceptron
    - The model and algorithm are the same, but we combine the inputs in a non-linear way in order to improve the model
        - For example, we can put in x, y, x sup>2</sup>, and xy and so on
        - This allows us to make funky circles and other shapes instead of just lines (like in 2D)
