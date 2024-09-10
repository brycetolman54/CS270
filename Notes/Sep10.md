# Finish Introduction

## Inductive Learning

- Input is a vector of features, nominal (discrete) or continuous (real)
- Output can be a scalar or vector of nominal or real values
- There are types of learning (this is inductive and is the most common)
    - Supervised, Unsupervised, Semi-supervised, and reinforcement
- There are others that we won't talk about

## Standard steps of Inductive Learning

1. Select Application
2. Select input features
3. Gather and prepare data
4. Train with learning model
5. Test learned hypothesis on novel data
6. Iterate until we get the outcome we desire

# Perceptrons

- There is only one output node (the output can be either 1 or 0)
- The inputs are all real values
- Each input has a weight (positive, negative, or 0)
    - We initialize these with small random values and then let them adjust as we go
- The <b>activation function</b> takes all the weighted inputs, sees if it hits the threshold, and then fires or not
- Then we have to adjust the weights or threshold in order to minimize the error of the perceptron (these iterations are called <b>epochs</b>)
    - How do we adjust the weights and threshold?
        - `&Delta;w<sub>i</sub> = (t<sub>i</sub> - z) * c * x<sub>i</sub>`
            - `t<sub>i</sub>` is the target value
            - `z` is the actual output value
            - `c` is the correction factor (We want to keep this small to avoid jumping over the answer and to ignore noisy data)
            - `x<sub>i</sub>` is the input value (to correct based on the effect the input was already having)
- We can have a <b>bias weight</b> that we initialize like other things. We then set the <b>threshold</b> to 0. This makes it so the other input nodes have to sum up to counteract the bias node in order to get an output
    - DON'T FORGET THE BIAS WEIGHT!!!

- Example:

- The learning rate is 1
- The activation function is just if the net input is greater than 0, we output 1, else we output 0
- Training set:
    - 0 0 1 -> 0
    - 1 1 1 -> 1
    - 1 0 1 -> 1
    - 0 1 1 -> 0

| Pattern | Target(t) | Vector(w<sub>i</sub>) |  Net  | Output(z) | &Delta;w<sub>i</sub> |
| :-----: | :-------: | :-------------------: | :---: | :-------: | :------------------: |
| 0 0 1 1 |     0     |       0 0 0 0         |   0   |     0     |      0  0  0  0      |
| 1 1 1 1 |     1     |       0 0 0 0         |   0   |     0     |      1  1  1  1      |
| 1 0 1 1 |     1     |       1 1 1 1         |   3   |     1     |      0  0  0  0      |
| 0 1 1 1 |     0     |       1 1 1 1         |   3   |     1     |      0 -1 -1 -1      |
| 0 0 1 1 |     0     |       1 0 0 0         |   0   |     0     |      0  0  0  0      |
| 1 1 1 1 |     1     |       1 0 0 0         |   1   |     1     |      0  0  0  0      |
| 1 0 1 1 |     1     |       1 0 0 0         |   1   |     1     |      0  0  0  0      |
| 0 1 1 1 |     0     |       1 0 0 0         |   0   |     0     |      0  0  0  0      |

- So we see that the only input that actually matters for the output is the first one

