# Machine Learning

## Concepts

* Hyperparameter
  hyperparameter in bayesian statistic and hyperparameter in ML is different concept.
  In bayesian statistic, hyperparamter is the parameter of paramtere.
  In ML, hyperparameter is paramter of the model, such as learning rate, K in k-means etc.

------------------------------------------
* [Parametric and Nonparametric Machine Learning Algorithms](http://machinelearningmastery.com/parametric-and-nonparametric-machine-learning-algorithms/)

## Learning Theory

[simple guide](https://mostafa-samir.github.io/ml-theory-pt1/)

## Model Evaluation

* ROC
  FPR vs TPR curve
* AUC
  Area under ROC curve
* KS
* confusion matrix
  * True mean predict correctly,
  * Positive means prediction is positive
  * Acuracy: T / ALL
  * Precision: TP/ Prediction Positive
  * TPR/Sensitivity/Recall: TP/ Condition Positive
  * FPR/fall-out: FP/ Condition Positive

## Model

### Tree Based Model

1. CART
  [Algorithm go over](http://machinelearningmastery.com/classification-and-regression-trees-for-machine-learning/)
  [Python code instruction](http://machinelearningmastery.com/implement-decision-tree-algorithm-scratch-python/)
  [Gini impurity vs information gain](https://www.quora.com/What-is-the-difference-between-information-gain-and-gini-index-When-should-I-apply-each-of-the-method)
  I think the most practical advice is to try both. Choosing entropy is better when your error metric is log-loss, in theory, since that’s what it’s trying to minimize.
2. Bagging (Random Forest)
3. Boosting (Adaboost,xgboost) 
  [adaboost algorithm](http://mccormickml.com/2013/12/13/adaboost-tutorial/)
  [adaboost papar](http://rob.schapire.net/papers/explaining-adaboost.pdf)
  [tutorial](https://www.analyticsvidhya.com/blog/2015/11/quick-introduction-boosting-algorithms-machine-learning/)
  [tianqi chen notes on xgboost](http://homes.cs.washington.edu/~tqchen/pdf/BoostedTree.pdf)
  [tutorial](https://www.zybuluo.com/yxd/note/611571)

* Reading
   [tree-based-modeling-in-python](https://www.analyticsvidhya.com/blog/2016/04/complete-tutorial-tree-based-modeling-scratch-in-python/)


### Logit

1. difference between probit(probability unit) 
2. [Parameter interpretation](http://www-hsc.usc.edu/~eckel/biostat2/notes/notes14.pdf)
3. [How to interpret model result](http://logisticregressionanalysis.com/1577-what-are-z-values-in-logistic-regression/)

## Feature Engineering
1. Why discretation
  [zhihu answer](https://www.zhihu.com/question/31989952)

[tutorial on data exploration](https://www.analyticsvidhya.com/blog/2016/01/guide-data-exploration/) 

## Questions

1. Multicollinearity
2. statistical learning vs maching learning
3. what is linear model

