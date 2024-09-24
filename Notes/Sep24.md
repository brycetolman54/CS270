# Avoiding Overfit

- We have a hypothesis set (H), we want to find the hypothesis (h) that gives us our best model
- How do we choose this and not overfit?
    - Occam's razor: choose the simplest model
    - Validation set
        - Split data into test, train, and validate
        - Train on train and then see how it does on the validate set
        - Make adjustments based on the train and validate accuracy (never the test set, that one can't be used to make decision on the algorithm)
        - Once the validate set starts to flatten out, stop the training
        - This is nice because you can run the validation on another process
    - Early stop
        - Do epochs (or training time, doesn't have to be epochs) until you get a low error on the train set

# Inductive Bias

- Approach to decide how to generalize to novel data
    - Common approach is Occam's razor: choose the simplest hypothesis that fits the data
- There is no inductive bias that is the best for all tasks. Each task has an inductive bias that works best for it
- How do we choose the inductive bias we need?
- Given some data, there are many possible hypotheses that we can use (or there may be). We can choose any of them and just guess which is best. 
- If we include a bias, we choose which hypothesis we are going to use (before we train the data). This tells us how to generalize to other things

# Feature Selection

- You want the data to be invariant
