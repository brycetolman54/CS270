# Quadric Machines

- Suppose we have data that isn't linearly separable (a line of points on the x axis from -3 to 3)
- We want to make that quadric to give more input so we can separate the data (do the input<sup>2</sup>)
- That makes a parabola and we can now separate the points 
- That is the idea: take the inputs, multiply them by one another to make more inputs, train on those with their targets

# Data Set Features

- Data types for inputs (or the outputs):
    - Nominal (categorical, discrete) - categories, not ordered -> like crust for a pizza
    - Continuous (Real, numeric) -> like cheese on a pizza -> like size of a pizza (like the diameter in inches)
    - Linear (Ordinal) - similar to nominal, but this is all ordered, it is treated like continuous -> like cheese on a pizza (a scale from 1 to 10 of amount)
    - For outputs:
        - Nominal output is what we call classification (which category does this thing apply to)
        - Continuous output is what we call regression (get a non set number)
    - Typecasting
        - Continuous to nominal -> put values in bins of different ranges
        - Nominal to Continuous -> see below
        - Linear data -> this is already continuous


# Moving Nominal data into Continuous data

- How do we address this problem?
    - Turn each nominal value into a node, set the node for the type of the data point to 1 and the others for the other types to 0
    - Keep the category as one node but assign the continuous values for the different types (1 for type 1, 2 for type 2,...)
    - Split into log<sub>b</sub>n binary nodes to represent the values in binary input (3 nodes for 8 values)

# Data Normalization

- What if we have a data set with only two input features that have wildly different magnitudes?
    - That won't work because one of the input sets is going to be huge and wildly overshadow the other
    - We normalize it like this: `f_normalized = (f_original - Minvalue_TS)(Maxvalue_TS - Minvalue_TS)`
        - Keep track of those max and min to use with novel data (That might give them a bit different values, but that's fine)

# ARFF File

- Comment section
- Metadata Section
    - Define the attributes (The features), it can only take nominal or continuous (linear is just continuous here)
- Data information
    - A comma separated list

```
% My ARFF File

@RELATION Pizza

@ATTRIBUTE Weight   real
@ATTRIBUTE Crust    {Pan, Thin, Stuffed}
@ATTRIBUTE Cheese   real (though it is actually linear)
@ATTRIBUTE Meat     {True, False}
@ATTRIBUTE Quality  {Good, Great}

@DATA
0.9,    Stuffed,    99,     True,   Great
0.1,    Thin,       2,      False,  Good
0.3,    Thin,       60,     True,   Good
...
```

- We need to be able to turn this into a perceptron data set
    - In this case, let's just explode the crust into a node for each (The other categoricals are already binary, so they are already good)

# Performance Measures

- Need to make sure future novel data shares the same distribution as the training data
- Training Set Method: 
    - Train on one set, then test accuracy on same data
    - This is not the best for generalization, but it is good to know how accurate it is learning what it is given
- Static Training/Test Set
    - Make the training set and distribute that
    - Keep a test set to see how the algorithm generates
    - Make sure that you don't overfit the test set (you can't use the test set or its accuracy to change the algorithm because that means you are fitting that test set)
- Those two are not the best. The next two are the ones we really want to use
- Cross-Validation
    - We split into test and train data (time and time again)
    - We change up the data that we are using for training and that we are using for testing
    - Random training/test set approach
        - Shuffle the data
        - Split into training and test
        - Train it and test it
        - Shuffle it
        - Split again
        - ...
    - Do tons of those runs, average the results of accuracy on the training, then you have statistics about how well it actually generalizes
    - You just reset the model every time
- N-Fold Cross Validation
    - Like above, but we split the data into <i>N</i> sets
    - Choose one to be the test set
    - Train on the rest
    - Do this where each set is the test set once
    - This gives us stats about generalization to novel data
    - You reset the data every time
    - To get the actual model to use (the above just gives you stats about generalization), just retrain it with all the data, leaving none out for testing (you do the same for the above approach)

# Perceptron Lab

- 
