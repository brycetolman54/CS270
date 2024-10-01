# More on Multilayer

- We don't have error near the boundary for our activation functions (it is sigmoid, the derivative is a nice peak)
- It makes sense that we only pass back error based on what the input to a node was
    - If a node is not passing input to a later node, that later node doesn't need to tell the earlier one that it needs to change, it doesn't care
- <b>Saturation</b> is when we have a larger or small value (not something by the threshold), because that is when we don't need to change anymore
- You want to start off with small, random weights and build from there
- The <b>inductive bias</b> of this model?
    - Start with a simple surface, increase in complexity until you just have a solution

- <b>Softmax Output Layer Activation</b>: This gives a probability for each class rather than just a class
    - $f(net_j) = {e^{net_j}} / {\sum_{i=1}^{n}e^{net_i}}$
    - That is for the output nodes only, the rest of the nodes still do a standard activation function (like ReLU, logistic, hyperbolic tangent)
- <b>Cross Entropy</b>: this is another type of loss function, this is what Sklearn uses
    - $Loss_{CrossEntropy} = -\sum_{i=1}^{n} t_i ln(z_i)$
        - $t_i$ is the target of the node
        - $z-i$ is the actual output
- Now the change in weights?
    - You just get $t-z$ (no $f(net_j)$) for the output layer
    - You can choose whatever function you want for the hidden layers

### Regression with MLP/BP

- We just use <i>sum-squared error</i> for the loss function
- We use a linear activation for the output nodes
    - The output error for these is $(t-z)f'(net)$, but since our function is a line, $f'(net)$
- Hidden nodes still use a non-linear function

## Local Minimum

- You don't have to worry about this. The more dimensions, the less likely there is a place where all dimensions are at a minimum that isn't the absolute minimum

## Hidden Nodes

- This all depends on what the problem is
- If it is linearly separable, we don't need any hidden nodes
- If it is simple, we need some nodes; if it is more complex, we need more nodes

## Learning Rate

- We have to modulate this correctly
    - If it is too high, we stay too high, since we are always jumping over the answer
    - If it is too low, we take forever to get there

## Momentum

- This is like an adaptive learning rate
- It is a speed-up modification
- We store previous updates to our weights, when we start to make the same or similar weight updates consecutively, we decide to actually just change the weight by more

## Hyperparameter selection

- You can't really just optimize one at a time, that doesn't work well
- We can use <b>Automated Hyperparameter Search</b>: tell the computer discrete values for each of the hyperparameters, the computer goes and tests each combo
    - The disadvantages: you need lots of time, you still don't know those ranges you should choose
    - We could also do a random search
        - You can specify the number of searches you will do
        - There's the possibility that you won't find anything good

## How to avoid overfit

- We take a validation set from the training set
- Test the model on the validation set and stop when there is no more improvement
- Change the sets of training and validation and test
- Keep the weights from the best results on validation (and the number of epochs from each validation set for convergence)
- Then take that model and train it on all the data (until the same point you trained the other ones, since you don't have a validation set now to know when to stop)
- That testing on the validation (you stop when it flattens) tells you when to stop and thus keeps the weights from overfitting the training set

## Backpropagation Lab

- with output, we don't need to return th
