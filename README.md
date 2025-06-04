A comparison of 4 different classifier algorithms using data from a Portuguese Banking Institution's marketing campaign (source: https://archive.ics.uci.edu/dataset/222/bank+marketing).

Logistic Regression, K Nearest Neighbors (KNN), Decision Tree, and Support Vector Machine (SVM) algorithms were used for the comparison. A baseline dummy classifer was also used to compare to random predictions based on the data distribution.

Comparing the default hyperparameter settings for all algorithms showed increased accuracy compared to the baseline classifier. However there were significant differences in computation time, namely for SVMs.

After comparing the default hyperparameters, GridSearchCV was used to optimize each algorithm. After performing this step, most models actually didn't improve much in terms of accuracy, with the exception of Decision Tree. The Decision Tree algorithm went from 84% accuracy to 90% accuracy. This was comparable to the SVMs accuracy, but with faster computation time.

The decision tree algorithm was then selected for further investigation, as it was still unnecessarily complex. The tree was pruned using cost complexity pruning. This was extremely effective and was able to reduce the tree from over 100 nodes to a mere 5, while maintaining nearly the same accuracy of 90%.

After pruning the decision tree, only two input features are needed to maintain 90% accuracy: 'age' and 'housing', where 'housing' is a categorical feature indicating if the client has a housing loan (note, it is not a binary field, as there are also "unknown" values).

Pruning also slightly reduces the number of false negatives, while slightly increasing false positives. This is an acceptable trade-off, because it means the business can target clients who would have potentially been missed, at the cost of a few more unsuccessful campaigns, in a field where the majority of campaigns are unsuccessful anyways.
