# Regression

- We want to find a hyperplane that approximates our data
- The input is mapped onto the hyperplane and then we get our output
- We use sum squared error (sum up the squared residuals) to get the difference
    - This gives us parabolic error curve, which is good for gradient descent
    - This always gives us the best fit
    - This is affected by outliers, since it is squaring the values

## Delta Rule

- We use `Δw = c(t - net)x_i`
    - Notice how we use net instead of output, since this is regression (the output is actually the net, but...)


| x<sub>1</sub> | x<sub>2</sub> | Target y |   Weights   | Output | deltaWeights |
| :-----------: | :-----------: | :------: | :---------: | :----: | :----------: |
|      0.5      |     -0.2      |     1    |    1    1   |   0.3  |  0.35 -0.14  |
|       1       |       0       |   -0.4   |  1.35 0.86  |  1.35  |  -1.75  0    |

- After one epoch, the weights are -0.4 and 0.86
- The delta rule converges to the best solution, always. So, we just go until the weights stop changing

- The nice thing about perceptron and regression is that they are intelligible. We can look at the weights and interpret them and understand them. Other models aren't so nice
- We have to make sure that we don't overfit our training data. How do we make sure we don't use the wrong order?
    - The error will go down and down, then it starts going up
    - We want to get it at that minimum in the error curve

## Regularization

- We want to keep the model simple but accurate
- We can see the model overfitting when there are more inputs. Furthermore, we can see it when the weights get huge. The weights have to get huge to get to all the points perfectly

- We want to minimize our loss function
    - We want to minimize error on our training set (not our test set), and the complexity of the model
        - e.g. `Minimize F(h) = Error(h) + λComplexity(h)`
        - We see complexity by summing all the weights (that means something with more inputs can be less complex than something with less weights)
        - $F(w) = TSS(w) + \lambda ||w||^2$
            - The TSS is sum of square error, λ is a constant
        - Then we take the derivative and we want to get the min of that
            - $\Deltaw_i = c(t - net)x_i - \lambdaw_i$
