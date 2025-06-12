## K-fold cross validation
Entire data is split into k subsets. The model is trained k times, each time using k-1 folds for training and the remaining fold for validation. While it allows every data point to be used in both training and validation, it has limitations. One limitation is that the models trained on different folds are not completely independent, affecting the reliability of the model performance. It is also limited by the fixed number of folds, which can reduce granularity of model evaluation.

## Bootstrap Aggregating: Bagging
The main idea is sampling with replacement, addressing the limitation of k-fold data split in generating as many subsets as possible. It estimates the distribution of the original data by generating statistic from each bootstrapped sample that has slightly different noise from each other. Due to its nature of sampling with replacement, it is both possible for an instance to be selected multiple times in different bootstrapped sample and not selected at all. Approximately, 2/3 of instances are sampled more than one time, and the remaining 1/3 of instances are not selected in any sample. The collection of instances that are sampled 0 times is called **out of bag (OOB) sample**. These OOB samples serve as built-in validation data. This enhances reliability of validation of the model. Bagging is useful for complex models with low bias and high variance (e.g. decision tree, NN, SVM)

## 🌲 Random Forest
Random Forest is a type of supervised learning and an ensemble method that builds many decision trees. It aggregates predictions of each tree to make a final decision. In **random forest classifier**, each tree votes for a class label, and the final decision is made by the majority vote. In **random forest regressor**, the prediction is made with the averaged value across all trees.

Individual decision trees are weak learners, and random forest makes them stronger by combining their predictions. Therefore, the variance is reduced and the results are generalized better with random forest.

---

## 📈 Gradient Boosting Machine
Gradient Boosting Machine (GBM) is an ensemble learning method that is based on sequential tree models that combine weak learners to generate a strong leaner (**Boosting**). Unlike random forest where individual trees are built independently, GBM trains models to correct the errors from the previous trees, using gradient descent. Gradient descent is a concept that minimizes the loss function in each iteration. 

Extreme Gradient Boosting, **XGBoost**, improves the traditional gradient boosting model's efficiency and scalability by applying regularization, parallelization, and enhanced approximation.

**LightGBM**, developed by Microsoft, has faster and more efficient computation approach than the traditional GBM with its unique optimization technique. Instead of evalutatng every possible split of features which leads to heavy computation in traditional GBM, lightGBM bins feature values into buckets, while maintaining high accuracy. There are two
**CatBoost**
**AdaBoost**


---

## Bagging


