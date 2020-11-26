**Gradient Boosted tree classifier**

**Content**

Table of contents

- [Gradient Boosted tree classifier](#gradient-boosted-tree-classifier)
  - [Introduction](#introduction)
  - [Development](#development)
    - [Concepts](#concepts)
    - [Components](#components)
    - [How does it work?](#how-does-it-work)
    - [Gradient boosting vs Adaptive boosting](#gradient-boosting-vs-adaptive-boosting)
    - [Visual example](#visual-example)
    - [Aplications](#aplications)
    - [GBRT](#gbrt)
      - [Advantages](#advantages)
      - [Disadvantages](#disadvantages)
  - [Conclution](#conclution)
  - [References](#references)

<div align="justify">

# Gradient Boosted tree classifier

## Introduction
In this repository, in the theory folder, the characteristics will be discussed, how the calculation is carried out and the considerations that are taken into account for the use of gradient-enhanced trees, as well as the purchase of other types of representations and mathematical calculations for compare their effectiveness and see their differences.
In the examples folder you will see an example taken from the spark page to see via code the application of the theory within our scala tool.
## Development
### Concepts
Gradient boosting is a machine learning technique for regression and classification problems that produce a prediction model in the form of a set of weak prediction models. This technique builds a model in a scenic way and generalizes the model allowing the optimization of an arbitrary differentiable loss function.
Boosting is another ensemble strategy that can be used with a wide group of statistical learning methods, including decision trees. The idea behind boosting is to sequentially fit multiple weak learners (simple models that predict only slightly better than expected by chance).
### Components
Gradient Boosting has three main components:

**1) Loss Function:** The role of the loss function is to estimate how good the model is at making predictions with the given data. This could vary depending on the problem at hand. For example, if we're trying to predict the weight of a person depending on some input variables (a regression problem), then the loss function would be something that helps us find the difference between the predicted weights and the observed weights. On the other hand, if we're trying to categorize if a person will like a certain movie based on their personality, we'll require a loss function that helps us understand how accurate our model is at classifying people who did or didn't like certain movies.

**2)Weak Learner:** A weak learner is one that classifies our data but does so poorly, perhaps no better than random guessing. In other words, it has a high error rate. These are typically decision trees (also called decision stumps, because they are less complicated than typical decision trees).

**3)Additive Model:** This is the iterative and sequential approach of adding the trees (weak learners) one step at a time. After each iteration, we need to be closer to our final model. In other words, each iteration should reduce the value of our loss function.

### How does it work?
Gradient Boosting basically combines weak students into one strong student in an iterative way. As each weak student is added, a new model is fit to provide a more accurate estimate of the response variable. Weak new students are most correlated with the negative gradient of the loss function, associated with the whole set. The idea of increasing the gradient is that a group of relatively weak prediction models can be combined to build a stronger prediction model.
### Gradient boosting vs Adaptive boosting
| Gradient boosting | Adaptive boosting | 
| --- | --- |
| This approach trains learners based upon minimising the loss function of a learner (i.e., training on the residuals of the model)  | This method focuses on training upon misclassified observations. Alters the distribution of the training dataset to increase weights on sample observations that are difficult to classify.| 
| Weak learners are decision trees constructed in a greedy manner with split points based on purity scores (i.e., Gini, minimise loss). Thus, larger trees can be used with around 4 to 8 levels. Learners should still remain weak and so they should be constrained (i.e., the maximum number of layers, nodes, splits, leaf nodes) | The weak learners incase of adaptive boosting are a very basic form of decision tree known as stumps. |
| All the learners have equal weights in the case of gradient boosting. The weight is usually set as the learning rate which is small in magnitude. | The final prediction is based on a majority vote of the weak learners’ predictions weighted by their individual accuracy. | 
### Visual example

The tree ensemble model consists of a set of classification and regression trees (CART). Here’s a simple example of a CART that classifies whether someone will like a hypothetical computer game X.

![Imgur](https://imgur.com/C0Q5uNQ.png)


We classify the members of a family into different leaves, and assign them the score on the corresponding leaf. A CART is a bit different from decision trees, in which the leaf only contains decision values. In CART, a real score is associated with each of the leaves, which gives us richer interpretations that go beyond classification. This also allows for a principled, unified approach to optimization, as we will see in a later part of this tutorial.

Usually, a single tree is not strong enough to be used in practice. What is actually used is the ensemble model, which sums the prediction of multiple trees together.



![](https://github.com/AdamariMosqueda/Gradient-boosted-tree-classifier/blob/master/images/example.png)


Mathematically it is expressed as follows:

**_If we have 2 trees, the predictions are added_**

But it can also be expressed as the sum of the last tree to what we already had added.

![](https://github.com/AdamariMosqueda/Gradient-boosted-tree-classifier/blob/master/images/math1.png)

This **ŷ** function is our prediction and we have to optimize it. For this we create an objective function (for example, based on the quadratic error) that we have to minimize:

![](https://github.com/AdamariMosqueda/Gradient-boosted-tree-classifier/blob/master/images/math2.png)


### Aplications
"Neurobiotics refers to the study of the nervous system in conjunction with technology. Of particular importance in the field of neurobiotics is the brain and its direct interaction with computer systems, as well as external brain simulation methods"


![](https://github.com/AdamariMosqueda/Gradient-boosted-tree-classifier/blob/master/images/neuro.png)


Gradient boosting is a handy tool for prediction tasks, and it consistently provides higher precision results compared to conventional machine learning models. For example, increasing the gradient helps create models that can map EMG and EEG sensor readings to human movement tracking and activity recognition.
### GBRT
GBRT is an accurate and effective business procedure that can be used for both regression and classification problems. Gradient Tree Boosting models are used in a variety of areas, including web search classification and ecology.
#### Advantages
- Natural handling of mixed data (heterogeneous characteristics)
- Predictive power
- Robustness to outliers in the output space (through functions of robust loss)
#### Disadvantages
- Scalability, due to the sequential nature of driving, it is difficult to
can parallelize.
The sklearn.ensemble module provides methods for classification and
regression through gradient-powered regression trees.
## Conclution
This type of tree helps us see 'where we are' and 'where we want to go' no longer seems to work, and things become more interesting.
As in the other types of prediction, this one helps us with training data and then with test data in order to have the least margin of error.
## References
- Cory Maklin. (2019). Gradient Boosting Decision Tree Algorithm Explained. 2020, de towardsdatascience Sitio web: https://towardsdatascience.com/machine-learning-part-18-boosting-algorithms-gradient-boosting-in-python-ef5ae6965be4
- Freddy Hernández. (2020). Gradient Boost. 2020, de github Sitio web: https://fhernanb.github.io/libro_mod_pred/gradboost.html
- Deepai. (----). Gradient Boosting. 2020, de deepai Sitio web: https://deepai.org/machine-learning-glossary-and-terms/gradient-boosting
- Autor Anónimo. (----). Gradient boosting. 2020, de wikipedia Sitio web: https://en.wikipedia.org/wiki/Gradient_boosting#:~:text=Gradient%20boosting%20is%20a%20machine,prediction%20models%2C%20typically%20decision%20trees
- VIHAR KURAMA. (2020). Gradient Boosting In Classification: Not a Black Box Anymore!. 2020, de paperspaceblog Sitio web: https://blog.paperspace.com/gradient-boosting-for-classification/
Sai Karthik. (2018). 2018. 2020, de medium Sitio web: https://medium.com/gradient-boosting-working-limitations-time/gradient-boosting-working-and-applications-28e8d4ba866d
- Autor Anónimo. (----). Neurobiotics. 2020, de wikipedia Sitio web: https://en.wikipedia.org/wiki/Neurobiotics
- Javier . (2019). Como funciona Gradient Boosting. 2020, de spainml Sitio web: https://spainml.com/blog/como-funciona-gradient-boosting/
</div>