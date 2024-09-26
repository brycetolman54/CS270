# Multilayer Learning

- The OGs were not too great, they really only had one layer that could learn
- What if we try backpropagation?
    - This allows us to learn weights at multiple layers rather than just one
    - This is a quick, easy way to compute the gradient!
    - We push the error back through the whole network, thus propagating the error backwards
- We have a problem. How do we know what direction to push the error propagation? We don't know anything from the layer before the last.

- When we have non-linearly separable data, we can draw one line with one input/node, then another with another input/node, etc.
    - That is where we get two layers. 
    - Then, to get the area encompassed by all the lines, we add another layer where all nodes in the second layer are inputs to that last layer. 
    - Now, we have multiple layers and multiple nodes and we have a space that works to separate our data
    - That last layer can be an `and` that takes those previous layer outputs as inputs. That is making it a linearly separable problem at the end.

- They started with a sigmoid activation function, instead of 0 and 1 with sharp turns between, we smooth the corners and make it so we can take the derivative
    - This makes the line that separates the data "fuzzy"

# Backpropagation Algorithm

- We find the (T)arget - Output (Z) for the output nodes
- We take that error and send it back to the hidden layer
- The Delta rule: $\Delta w_ij = C \delta _j Z_i$
    - $C$ is the learning rate
    - $\delta_i$ is the error (changes for output/hidden nodes)
    - $Z_i$ is the output from node i to j
- What does the function look like?
    - Sigmoid: $Z_j = f(net_j) = 1 / (1 + e^(-net_j))$
    - The derivative = $f'(net_j) = Z_j (1 - Z_j)$
    - The derivative doesn't change so much at the edges, but does at the center. That is good. We don't want it to change much when we are quite close to the right answer.
- Learning Equations:
    - For an output node: $\delta _j  = (T_j - Z_j)f'(net_j)$
    - For a hidden node: $\delta _j = \sum_{k} (\delta _k w_jk)f'(net_j)$
- What are i, j, and k?
    - i is the node behind us
    - j is the one we are at
    - k is the one we are looking forward to
- We need to have a bias node in each layer (it is not affected by the previous layers, it comes new in each layer)
    - So, a 4-2-2 network will have 5 nodes in the first layer, 3 in the next, and 2 in the next
    - The first layer has all nodes go to only 2 in the next
    - The second layer has 5 inputs each except for the bias node
