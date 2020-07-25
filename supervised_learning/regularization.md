# Regularization in Neural Networks

This is a form of regression, that constrains/ regularizes or shrinks the coefficient estimates towards zero. In other words, ***this technique discourages learning a more complex or flexible model, so as to avoid the risk of overfitting.***

Lets say $LF_n$  is our loss function, then after applying a regularization function the final function which needs to be optimized becomes: 

$$LF_n + RegF_n$$

We have the following types of regularization:

- L1
- L2
- Early Stopping
- Dropout
- Batch Standardization
- Training Knowledge Augmentation
- Group Lasso
- Sparse Group Lasso
- Elastic Net regularization



## Lasso Regularization

$$\Large RegF_n = \lambda\sum_{i=1}^{n}|w_i|$$

aka ***L1 regularization***



## Ridge Regularization

$$\Large RegF_n = \lambda\sum_{j=1}^{p} w_j^2$$

or

$$\Large RegF_n = \lambda\sum_{j=1}^{p} ||w_j||_2$$ where $||w_i||_2$ is the ***Froenius value*** 

Aka the ***L2 regularization***

L1 (also called as Lasso) decreases the weights until they become Zeros, in that way preventing the Overfitting, this method is useful if we want to compress the entire algorithm, it can create a sparse model, and It is fast in terms of inference and fitting.

### L1 vs L2

L2 (ridge or weights decay) decreases the weights towards Zero but they don't become Zero, in that way avoiding the overfitting. Some advantages are that L2 is better than L1, Ridge adds just enough bias to make the estimates reasonably reliable approximations to true population values and it is especially good at improving the least-squares estimate when multicollinearity is present. 

In some cases the model selected by L1(lasso) is not stable, the model selection result is not intuitive to interpret and its prediction performance is usually worse than weights decay regularizer.

L2 doesn't perform feature selection, it doesn't create a sparse model, it is not useful to compress your model.

> The **key difference** between these techniques is that Lasso shrinks the less important feature’s coefficient to zero thus, removing some feature altogether. So, this works well for **feature selection** in case we have a huge number of features.



## Early Stopping Regularization

<img src='../assets/early_stopping.png' />





## Dropout Regularization

It is also another regularization technique, that consists of turning on and off randomly selected neurons. In this way, preventing the overfitting because as the neurons will be randomly selected and the weights will also be randomly changed, therefore the Neural Network won't be affected by the high weights.

The pros of this technique is that it creates random groups and in this way prevents all the neurons from converging to the same goal and the activation of the hidden units becomes sparse.

 Cons for this technique is that one can apply this technique into Neural Networks but not with every algorithm like L2 or L1.



## Training Knowledge Augmentation

This method involves creating more data from the existing data. It can be easily done with image input data. Most common techniques include basic trasnformations like skewing the input, translating in horizontal and vertical plane, flipping horizontally or vertically, cropping, scalling and rotating along some point.



## Batch Normalization

 