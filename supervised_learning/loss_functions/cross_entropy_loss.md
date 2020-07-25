# Cross Entropy Loss

## aka Negative Log Likelihood



## Mathematical Formula

### For Binary Classification

$$\LARGE CrossEntropyLoss = - \frac{1}{m}\sum_{i=1}{m}(y_ilog(\hat{y}_i) + (1-y_i)log(1-\hat{y}_i))$$

### For MultiClass Classification

$$\LARGE CrossEntropyLoss = - \frac{1}{m}\sum_{i=1}^{m}y_ilog(\hat{y}_i)$$



## Explanation

Cross-entropy loss increases as the predicted probability diverges from the actual label.

Notice that when actual label is 1 (y(i) = 1), second half of function disappears whereas in case actual label is 0 (y(i) = 0) first half is dropped off. In short, we are just multiplying the log of the actual predicted probability for the ground truth class.

> ***An important aspect of this is that cross entropy loss penalizes heavily the predictions that are confident but wrong***

<img src='../assets/cross_entropy.png' />