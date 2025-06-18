---
## 🔁 K-fold cross validation
Entire data is split into k subsets. The model is trained k times, each time using k-1 folds for training and the remaining fold for validation. While it allows every data point to be used in both training and validation, it has limitations. One limitation is that the models trained on different folds are not completely independent, affecting the reliability of the model performance. It is also limited by the fixed number of folds, which can reduce granularity of model evaluation.

---


## 🎲 Bootstrap Aggregating: Bagging
The main idea is sampling with replacement, addressing the limitation of k-fold data split in generating enough subsets. It estimates the distribution of the original sample by generating a statistic from  bootstrapped samples that have slightly different noise from each other. Due to its nature of sampling with replacement, it is both possible for an instance to be selected multiple times in different bootstrapped samples and not selected at all. Approximately, 2/3 of instances are sampled more than one time, and the remaining 1/3 of instances are not selected in any sample. The collection of the instances that are sampled 0 times is called **out of bag (OOB) sample**. These OOB samples serve as built-in validation data. It enhances reliability of validation of the model by utilizing the entire dataset in either training or testing. Bagging is especially efficient for complex models with low bias and high variance (e.g. decision tree, NN, SVM), but can be used for any type of learning methods.

- Bagging results aggregating 
for classification
  * Majority voting
  * Weighted voting based on OOB accuracy of individual models
  * Weighted voting based on predicted probability for each class
  * Stacking: using another prediction model (i.e. meta learner) to aggregate the result. It uses prediction from ensemble members as input and the actual true label as target.
  * etc.. (it is possible to create weights in combination of OOB accuracy and predicted probability

---
## 🌲 Random Forest
Random Forest is a decision tree based **bagging** learning. The core concept of an ensemble method is to increase the diversity of ensemble members. Random forest builds many decision trees (bagging; sampling with replacement) by randomply selecting predictor variables. Bagging is explained above. In any bootstrapped sample with n number of features, features are randomly selected to split trees. This increases the diversity one step further on top of bagging method, as splits with randomply selected predictors generate more various outputs, compared to trees built with all features. This strategy improves prediction accuracy, because it focuses on overall strength of the predictors rather than individual features.

Random forest is unique in that it calculates **variable importance**.
- How does it calculate variable importance?
  Let's say one of the features, Xi is being tested for its importance.
  * Step 1. compute the OBB error (ei) for Xi in the original dataset
  * Step 2. perform permutation (rearrange the order of values of Xi), then compute the OBB error (pi) for Xi the permuted dataset
  * Step 3. compute the variable importance based on the mean and standard deviation of (pi - ei, as pi > ei since permuted dataset generates higher error) over all trees in the population
     - if the Xi's importance is low (meaning Xi was never selected in both datasets of step 1 and step 2 because of unimportance), the value (pi - ei) would be 0.
     - the higher the Xi's importance is (meaning Xi was selected many times in both datasets of step 1 and step 2 because of importance), the value (pi - ei) would be larger.
     - if Xi's importance is higher, the mean of the value (pi - ei) would be higher across all trees, but the standard deviation would be lower.

It aggregates predictions of each tree to make a final decision. In **random forest classifier**, each tree votes for a class label, and the final decision is made by the majority vote. In **random forest regressor**, the prediction is made with the averaged value across all trees.

Individual decision trees are weak learners, and random forest makes them stronger by combining their predictions. Therefore, the variance is reduced and the results are generalized better.

---
## Boosting
Boosting: when a model only performs slightly better than random guessing, the model is a **weak learner**. The weak learner could be **boosted** in to arbitrarily accurate strong model. Compared to bagging, where multiple learners learn about a topic with slightly different materials at the same time and aggregate the output to determine the final decision, boosting occurs sequentially.

---
## 🧮 AdaBoost
In AdaBoost, "shortcomings" are identified by high-weight data points. AdaBoost lets the next model to focus on the difficult cases of previous models by assigning larger weights to misclassified data points, focusing to strengthen weak points of each learner in the next step.

--- 
## 📈 Gradient Boosting Machine
In GBM, "shortcomings" are identified by gradients. Gradient descent is a concept that minimizes the loss function in each iteration. 

First, an additive model (ensemble) is fitted in a forward stage-wise manner. In each stage, a weak learner is introduced to compensate the shortcomings of existing weak learners. Both high-weight data points and gradients tell us how to improve the model.

**Regularization** is important as GBM has a high risk of overfitting. Regularization techniques include subsampling, shrinkage, and early stopping.

As in random forest, GBM can provide feature importance, in a simpler way:
1. Calculate the importance of the variable j in a single tree T by summing the information gain of the variable in all splits of the tree. 
2. Sum all importances of the variable in individual trees, then divide it by the number of trees to get the importance of variable j.
   

---

## 🚅 Extreme Gradient Boosting
**XGBoost**, improves the traditional gradient boosting model's efficiency, scalability, and speed by applying regularization, parallelization, and enhanced approximation. XGBoost enables parallel processing by using the two algorithms.

1. Basic greedy algorithm for split finding: can always find the optimal split by observing every possible split point, but can be problematic when the large data cannot be viewed at once; impossible in a distributed setting.
2. Approximate algorithm (histogram based): spliting sorted data by tree level (global) or node level (local) by buckets (bins), reducing splitting time and increasing efficiency.

XGBoost can handle missing values by using **Sparsity-Aware Split Finding**, by setting default direction for missing values, which significantly reduces processing time.


## 🛠️ Light Gradient Boosting Machine
**LightGBM**, developed by Microsoft, has faster and more efficient computation approach than the traditional GBM with its unique optimization technique. Instead of evalutatng every possible split of features which leads to heavy computation in traditional GBM, lightGBM bins feature values into buckets, while maintaining high accuracy. There are two main techniques LightGBM utilizes to reduce the number of data instances to scan and to reduce the number of features to scan.

1. Gradient-based One-Side Sampling (GOSS): focuses on sample instances based on their gradients, prioritizing those with larger gradients. 
2. Exclusive Feature Bundling (EFB): increases efficiency by bundling features that are exclusive, maintaining performance accuracy.


![image](https://github.com/user-attachments/assets/de305234-3a3d-4f3c-9612-b5b117037557)

https://medium.com/data-science/https-medium-com-vishalmorde-xgboost-algorithm-long-she-may-rein-edd9f99be63d


