# DATA
Here, we are trying to find the relationship among various features so that we can extract only those features which has high weightage to the column 'Total Percentage'
# Feature-Extraction

In order to find the correlation between different variables, following steps were taken:

1. Explotary analysis of the data is done to remove null values, if any
2. Data is classified into 4 category on the basis of percentile of column 'total percent'
3. Plotting sctaterplot and finding correlation between data, No correlation was seen among the data
4. Then  we used random forest to find any non-linear relation among the data.


# What is Random Forest?
Random forests are bagged decision tree models that split on a subset of features on each split. This is a huge mouthful, so let’s break this down by first looking at a single decision tree, then discussing bagged decision trees and finally introduce splitting on a random subset of features.

# Why is Random Forest So Cool?
Whether we have a regression or classification task, random forest is an applicable model for our needs. It can handle binary features, categorical features, and numerical features. There is very little pre-processing that needs to be done. The data does not need to be rescaled or transformed.



# What is Hyperparameter Tuning

The best way to think about hyperparameters is like the settings of an algorithm that can be adjusted to optimize performance, just as we might turn the knobs of an AM radio to get a clear signal. While model parameters are learned during training — such as the slope and intercept in a linear regression — hyperparameters must be set before training. In the case of a random forest, hyperparameters include the number of decision trees in the forest and the number of features considered by each tree when splitting a node. (The parameters of a random forest are the variables and thresholds used to split each node learned during training)

Hyperparameter tuning relies more on experimental results than theory, and thus the best method to determine the optimal settings is to try many different combinations evaluate the performance of each model.

# We tried adjusting the following set of hyperparameters:
n_estimators = number of trees in the foreset
max_features = max number of features considered for splitting a node
max_depth = max number of levels in each decision tree
min_samples_split = min number of data points placed in a node before the node is split
min_samples_leaf = min number of data points allowed in a leaf node
bootstrap = method for sampling data points (with or without replacement)

On each iteration, the algorithm will choose a difference combination of the features.  However, the benefit of a random search is that we are not trying every combination, but selecting at random to sample a wide range of values.

# Model Training
First we used RandomForestRegressor to train the model and predict the total percent in the test data where the accuracy was only 64%.
Then we used RandomForestClassifier to do the same and got maximum accuracy of 98.4% after tuning parameters and we realized that though below features have more impact than others, there is no strong relation among any features and hence, we cannot remove any features. To confirm this, we trained the model with top 7 features and the accuracy decreased from 98.4% to 70%
# Top 4 features
Time Outside of 7 AM to 7 PM	0.122006
Messages Received per Day - Patient Calls	0.093028
Time in In Basket per Day	0.089402
Proficiency Score	0.088

