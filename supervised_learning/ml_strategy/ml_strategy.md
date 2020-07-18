# Machine Learning Strategy

## Orthogonalization

## Setting a goal

As outlined above, you need a clear goal to determine if a model is performing well. Hence the importance of setting an evaluation metric, as well as satisficing and optimizing metrics.

### Single Evaluation Metric

Having a single evaluation metric allows for quicker assessment of an algorithm.

For example, it is common to use precision and recall for a classifier. However, there is a trade off between these two metrics. Instead, use the F1 score, which is the harmonic mean of the precision and recall. Thus, a single metric is used, and it becomes much easier to assess the quality of different models and it speeds up iterations.

### Satisficing and optimizing Metrics

Once you have a single evaluation metric, it is common to track other important metrics.

For example, you might want to build a classifier with an F1 score of at least 0.90 and a runtime of less than 200ms. In this case, the F1 score is the **optimizing** metric, while the runtime is the **satisficing** metric.

An optimizing metric will usually be the same as your evaluation metric, and you should only have one optimizing metric. The other metrics of interest will be satisficing metrics, and will help you choose the overall best model that satisfies the optimizing metric.

## Training, Validation and Test set

Validation set is often also referred as the Development set.

The training and development \(or holdout\) sets are used to train a model. The training set is usually used to fit the model to the data, and the development set is used to make predictions and tweak the model.

Then, the test set is an example of real-life data on which you test the algorithm to see how it would perform.

### Distribution

Always make sure that in case of classification, the percentage of each label in training, validation and test set are same i.e if there are 6% cases of a label in training set, the same should be in case of validation and test set also.

Typically the split is 60-20-20 for training, validation and test set for small dataset.

However, in the case where you have millions of instances, a more appropriate split would be 98/1/1, because the model can still be validated on more than 10 000 data points.

## Comparing to Human Level Performance

In the case that your model is overfitting, you mus reduce variance by:

* Collecting more data
* [Regularization](https://towardsdatascience.com/how-to-improve-a-neural-network-with-regularization-8a18ecda9fe3) \(L2, dropout, data augmentation\)
* Change the model

In the case that your model is underfitting the data, you must then reduce bias by:

* Training a bigger or more complex model
* Use a better optimization algorithm or train for a longer time
* Change the model

