# Data

- We want labeled data
    - If your data doesn't come with labels already, you can get experts or do something like unsupervised learning to get those labels
- How to improve performance?
    - Get more data
    - Get better input features
    - Use a different model or hyperparameters
- We already worked with turning nominal into continuous. How do we transform continuous into nominal?
    - We can break the continuous values into bins of certain width (suffers from outliers)
    - We could also do bins of certain height (could split up things that should be grouped)
    - we could also do clustering, though this is more time and work to do (though it is more accurate)
    - There can be a problem on the borders, since two points right next to one another on the border lose that information when split into their respective bins

## Normalizing Data

- This is for continuous values, and we usually normalize to be between 0 and 1 or -1 and 1
    - This could be affected by outliers and skew
        - We can use a z-score to account for this (subtract mean and divide by standard deviation)
    - If we have skewed data, we can use a nonlinear normalization to account for that
        - You have to look at your data
- This keeps any one feature from dominating the rest because it has such large values compared to the other features

## Output Class Skew

- If you are undersampling, you can keep all of the minority class and get rid of some of the majority class
- If you are oversampling, make duplicates of the minority instance and use that
- You don't want to have 50/50
    - You don't want to throw out a ton of good data (when undersampling)
    - You don't want to see the same cases too much (when oversampling)
- Use Precision/Recall or ROC instead of accuracy when looking at the data and performance
- You could also make the model overweight the minority class so it has more of an effect on the learning

## Transformed/Derived Variables (meta-features)

- Take the old features, combine and transform them, get less features and get better learning
    - This could be something like a quadric machine
    - See if you can use only part of the data (like an area code instead of the whole phone number)
    - Try to combine the data (like height and weight into BMI)

## Relevant Data

- Obviously we want data that is relevant to the problem we are trying to solve
- Don't use features where:
    - All instances have the same value
    - All instances have different values (and the data for that is nominal)
    - Two features are highly correlated

## Missing Data

- We will often have missing data. What do we do?
    - We could throw it all out, but then we could lose a lot of data
    - We could impute the data (set its value to the mean or mode of the rest of the values), but that is making a big guess
    - We could use a learning scheme, change that value that is unknown to the thing that we are looking for (we can't factor in the output to this, though, because that is what we are looking for in execution)
        - This is not great because it takes more time and requires another model, but also we could have multiple unknowns and we would then have to deal with that
    - We could train multiple models with different numbers of features and use those when we are lacking that input info
    - We could let that category have an unknown value and train with that, this is a good option and the unknown can have a good cause that we can learn from
        - For nominal data, this is easy, just make another category for unknown
        - For continuous, we can:
            - Use a value that is not in the range of normal data
            - Use an indicator node that inputs 0 for data that is known and 1 for data that is unknown (we just put 0 or the mean or something for the missing data)
                - Hopefully the algorithm learns to ignore that missing data when the indicator node has a 1 as the input

## Bad/Dirty Data

- This can come from all sorts of places
- How do we clean?
    - We can look at the data and find mistakes or outliers
    - We can cluster or bin to take care of it
    - Experiments show that removing that data (noise or outliers) will improve subsequent accuracy
        - You could make a model to predict outliers based on the other features

## Labeled and Unlabeled Data

- You want accurately labeled data (junk in, junk out)
- You can use semi-supervised learning:
    - Augment a small set of labeled data with a lot of unlabeled data
