# Bayes

- How do we learn/train the model?
    - Bayes is just a regularization technique, to choose the model we want
    - Choose a hypothesis $h$ from all possible $H$ hypotheses
        - Each $h$ is the model (could be an MLP, a decision tree, etc.), just a model
            - If it were an MLP, each new model with distinct weights is its own model
    - $D$ is all the training data
    - $P(h|D)$ - the posterior, what we want to learn
    - $P(h)$ - the prior probability $h$ independent of $D$
        - We could give all $h$ equal probability
        - We could assign weighted probability (based on an inductive bias: e.g. the simpler the better)
    - $P(D|h)$ - the likelihood of data given the hypothesis
        - We just use the accuracy of our model $h$ on $D$ (or we can, this is one way, but it is what we usually do)
    - $P(D)$ - the probability of the data set, we don't really need this
- We want to find the best $h$ for our Bayes Rule:
    - $h_{map} = argmax_{h \in H}P(h|D) = argmax_{h \in H}P(D|h)P(h)/P(D) = argmax_{h \in H}P(D|h)P(h)$
        - This is the <b>Maximum a posteriori</b> (MAP)
    - $argmax_{h \in H}P(D|h)$
        - This is the <b>Maximum Likelihood</b>
    - How do we find all the $h$ in $H$ since there are an infinite amount of them?
- Prior handles overfit (the simpler model is chosen, so we can't overfit)
- This leads us to the <b>Bayes Optimal Classifier</b>: the best question is which class should a new instance belong to?
    - We let all hypotheses vote, then weight their answers by their posterior
    - $P(c_j|D,H,x) = \sum_{h_i \in H}{P)c_j|x, h_i}P(h_i|D) = \sum_{h_i \in H}{\frac{P(c_j|x, j_i)P(D|h_i)P(h_i)}{P(D)}}$
    - $c_{BayesOptimal} = argmax_{c \in C}\sum_{h \in H}{P(c_j|x, h_i)P(D|h_i)P(h_i)}$
        - This is how we find the most probable class $c \in C$ the new instance belongs to, with the <b>Bayes Optimal</b>
    - What is the problem?
        - We can't test infinite hypotheses
        - We can't know the priors super well

# Naive Bayes

- $P(c|x) = P(x|c)P(c)/P(x)$
    - $P(c)$ - Prior, how often the class is in our dataset
    - $P(x|c)$ - Likelihood of seeing data vector $x$ given that we have the class $c$
        - The problem is that our data sets are not really things that repeat (We can't just look at each c and say "oh, how many times do we see this class with this data set", it's probably just the one time we see that)
    - Why is it Naive? We assume:
        - $P(x_1, ..., x_n|c_j) = \prod_{i}{P(x_i|c_j)}$
        - Assume the likelihood of the data vector given the class is just the product of each feature's probability given the class
    - $c_{NB} = argmax_{c_j \in C}P(c_j)\prod_{i}{P(x_i|c_j)}$
    - With nominal data, getting the $P(x_i|c_j)$ is easy

## Example

| Size (L, S) | Color (R, G, B) | Output (P, N) |
| :---------: | :-------------: | :-----------: |
|      L      |        R        |       N       |
|      S      |        B        |       P       |
|      S      |        G        |       N       |
|      L      |        R        |       N       |
|      L      |        G        |       P       |

|  Probability Name | Probability |
| :---------------: | :---------: |
|        P(P)       |     2/5     |
|        P(N)       |     3/5     |
|   P(Size=L\|P)    |     1/2     |
|   P(Size=S\|P)    |     1/2     |
|   P(Size=L\|N)    |     2/3     |
|   P(Size=S\|N)    |     1/3     |
|   P(Color=R\|P)   |     0/3     |
|   P(Color=G\|P)   |     1/2     |
|   P(Color=B\|P)   |     1/2     |
|   P(Color=R\|N)   |     2/3     |
|   P(Color=G\|N)   |     1/3     |
|   P(Color=B\|N)   |     0/3     |

- Relative probabilities:
    - P(P|L,B) = P(P) * P(Size=L|P) * P(Color=B|P) = 2/5 * 1/2 * 1/2 = 1/10
    - P(N|L,B) = P(N) * P(Size=L|N) * P(Color=B|N) = 3/5 * 2/3 * 0/3 = 0
- True probabilities:
    - P(P|L,B) = 1/(1+0) = 1
    - P(N|L,B) = 0/(1+0) = 0
