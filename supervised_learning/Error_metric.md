# Error Metrics

We usually opt for the accuracy as our metric when we train our model and keep a look at our validation set accuracy for hyperparameter tuing.

But sometimes we might need the help of other error metrics to understand our model’s capabilities. 

One such case is in the case of **skewed dataset**, i.e. a dataset for classification but the examples for each class are not equal and one of the class’s examples are way to high compared to others that it dominates the other classes. Lets say we have a dataset where 95% exmaples belong to Class 0 and 5% exmples belong to Class 1. In this case if our model constantly predicts that it is Class 0, it will still have an accuracy of 95% because 95% examples belong to class0 and the model is wrong only for 5% of the examples.

 

## Precision/Recall Metric

Here we divide our training prediction into 4 categories

| Prediction\Actual | 1              | 0              |
| ----------------- | -------------- | -------------- |
| **1**             | True Positive  | False Positive |
| **0**             | False Negative | True Negative  |

- *True Positive*: Actual class was 1 and prediction was also 1
- *False Positive*: Actual class was 0 but prediction was 1
- *False Negative*: Actual class was 0 but prediction was 1
- *True Negative*: Actual class was 0 and prediction was also 0



In this case we would prefer our model to have more of True Positive and True Negative and less of False Postive and False Negative.

### Precision

$$\begin{align} \large Precision = \frac{\#True Positive}{\#Predicted Positive} = \frac{\#True Positive}{\#True Positive + \#False Positive} \end{align}$$

### Recall

$$\begin{align} \large Recall = \frac{\#True Positive}{\#Actual Positive} = \frac{\# True Positive}{\#True Positive + \#False Negative} \end{align}$$



$$\Large F\ Score\ (or \ F_1\ Score) = 2*\frac{P*R}{P+R}$$



