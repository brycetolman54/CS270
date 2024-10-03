# MLP Networks and Backpropagation

## Rectified Linear Unit (ReLU)

- This is an activation function
- Below 0, it is 0 and above 0 it is just linear with x
- The derivative at the point is not defined, but we just say it is 0 if it is there
- This makes backpropagation easy, since the derivative is either 1 or 0
- You can have a leaky where below 0 it is also linear, but with a different slope than the positive side


## Debugging ML Models

- Start with a simple example, you should know what it should do in those problems, so you can compare


## What are the hidden nodes doing?

- Interesting examples:
    - Take a sentence as input, have a lesser number of hidden nodes than are words in the sentence, try to get the same sentence on the other side
        - You will learn something about the structure of language (it has to maintain the structure and such but with less nodes at the center)
    - Take an image, pass it down into successive layers of lesser nodes, get down to 4 or 5 nodes, then re-expand it to get back the same image
        - You will have a compression method (run your picture through the first half, give it someone who runs it through the back half)
- We want to look at weights and outputs from the hidden nodes to learn about what they're doing, but it can be very hard to interpret what they mean


## Batch update

- On-line (Stochastic) update updates the weights after every pattern
- Batch update holds on to the changes until the end of the epoch and then updates every weight once at the end of the epoch
- Batch is not better. It computes a correct gradient (where stochastic may compute a wrong direction one for a given pattern), but it still has to take a tiny step and recompute.
    - Batch takes forever since it takes us forever to get the gradient, but we still take a tiny step
    - Sure, stochastic may take us into a local minimum, but those aren't really a problem in higher dimensions


## Local vs. Distributed Representations

- Local thinks one node remembers one thing
    - Remove a node, lose a memory
- Distributed things multiple nodes remember multiple things together
    - Remove a node, don't lost a whole memory
- We could force a local model in a way by having a sparse network


## Multiple outputs

- Say you have multiple outputs for a network, how do you deal with that?
    - You can train a network with the same nodes for each output
    - You can train them all in one and have separate hidden layers for each output
    - You can train them all in one and have the same hidden layers for each output


## Recurrent Network

- You take some of the output and put it back in as input
- You take some of the hidden layer output and put it back in as input


# Features

- We need to know what features to use in training our model
- We need these to be easy to calculate
- Say we are interested in looking at pictures of characters and trying to decide what they are
    - We don't want a ton of features (we don't want to just input all the pixels)
    - We want the inputs to be robust (so we can do something like "jiggle" the data, move the character, and not have the features change entirely)
