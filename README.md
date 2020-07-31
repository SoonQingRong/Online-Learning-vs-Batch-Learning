# Online-Learning-vs-Batch-Learning
Comparing the accuracy of Online Learning and Batch Learning

# What is Online Learning
Online Learning is a model training technique that gives the model the training data one sample at a time instead of the whole batch to fit which is what Batch Learning does. Online Learning has some advantages over Batch Learning such as if the training data is too huge to fit into memory to be able to train the model in one run, or if the model is preferred to predict data based on the most recent information.

# Project Aim
This project aims to compare the accuracy between Online Learning and Batch Learning to see the difference in accuracy between the 2 different training methods.

# Methodology
There will be 3 datasets and 3 different classifiers to perform the tests on.

The 3 datasets are Iris, Breast Cancer and Digits from Sklearn's datasets.

The 3 classifiers are the SGD Classifier, Perceptron and Passive Aggressive Classifier from Sklearn's linear model library.

Each of the test sets would be fed to 3 different base models instantiated from each of the 3 classifiers where:

1. Model 1 will undergo full online learning, being fit one sample at a time

2. Model 2 will first undergo online training on 50% of the batch, and then it will undergo online training for the remaining 50%, being fit one sample at a time

3. Model 3 will undergo batch learning, being fit the whole batch at a time

The test will be performed on the datasets that is splitted using 10-fold cross validation and their average accuracy across the 10 folds and graphs will be in the output for comparison.

# Explanation of shuffling the indexes of data twice
There are 2 random shuffles in the program for the indexes of the training and testing data

The first random shuffle that occured in the K-Fold argument was so that the test data indexes are not necessarily consecutive numbers as some datasets (e.g. Iris dataset) arranges data whose labels are the same close to each other. Applying shuffle = True in K-Fold would ensure that the the train and test data are not completely of 1 specific label to reduce biasedness.

The second random shuffle that occured after splitting the data in each iterations of the fold was so that the order the model would be learning the train data would be random as well. This is especially important for online learning models as these learning methods place greater emphasis on data that it was trained on near the later stage of its learning and some datasets (e.g. Iris dataset) arranges data whose labels are the same close to each other and that the model will overfit on that particular training class if given a huge amount of train data on that particular class consecutively. Shuffling the train indexes will randomise the order in which train data will be given to the model for online learning which will reduce biasedness.

# Conclusion
Batch learning models generally perform better than models using online learning based on the average accuracy across all 10 folds for all 3 datasets and all 3 different classifiers.
