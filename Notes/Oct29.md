# Data mining

- There is a lot of data that we can look through. The data could have useful information. But we can't go through it. So, we use applications to go through it for us.
- Here is the process model:
    1. Identify the task
    2. Gather data
        - Analyze the data, clean it, etc.
    3. Build and evaluate the model
    4. Deploy and evaluate the model
        - Visualization and such
    5. Iterate through to improve

# Bayesian Learning

- Baye's Rule:
    - $P(c|x) = \frac{P(x|c)P(c)}{P(x)}$
        - $P(c)$ is the <b>prior</b>, what we know from past info (independent of all the features, $x$)
            - $c = \frac{N_{class}}{N_{total}}$
        - $P(x)$ is the <b>prior probability</b> of the data vector(the features), $x$
            - We usually drop this. We don't actually need it, it is just a normalization factor. We care more about how $c$ affects $P(c|x)$
        - $P(x|c)$ is the <b>likelihood</b> of the features, $x$, given the class $c$
- Example:
    - We have 100 examples, 80 are good, the others are bad.
    - What are the priors:
        - $P(G) = 0.8$, $P(B) = 0.2$
    - What are the likelihoods:
        - $P(x|G) = 0.3$, $P(x|B) = 0.4$
    - So to find the probabilities:
        - $P(G|x) = 0.3 * 0.8 = 0.24$
        - $P(B|x) = 0.4 * 0.2 = 0.08$
        - We are more likely to have a good pizza
