# Support Vector Machine

A support vector machine is a generalization of a classifier called **maximal margin classifier**. The maximal margin classifier is simple, but it cannot be applied to the majority of datasets, since the classes must be separated by a linear boundary.

Support vector machine is simply a further extension of the support vector classifier to accommodate non-linear class boundaries.

It can be used for both binary or multiclass classification or even for regression but mostly it is used for classification.



## Advantages and Disadvantages

### Advantages

- It works really well with a clear margin of separation
- It is effective in high dimensional spaces.
- **It is effective in cases where the number of dimensions is greater than the number of samples.**
- It uses a subset of training points in the decision function (called support vectors), so it is also memory efficient.

### Disadvantages

- It doesn’t perform well when we have large data set because the required training time is higher
- It also doesn’t perform very well, when the data set has more noise i.e. target classes are overlapping
- SVM doesn’t directly provide probability estimates, these are calculated using an expensive five-fold cross-validation. 



## For Linearly Seperable Values

> The objective of the support vector machine algorithm is to find a hyperplane in an N-dimensional space(N — the number of features) that distinctly classifies the data points.

<img src='../assets/svm_2.png' />

To separate the two classes of data points, there are many possible hyperplanes that could be chosen. Our objective is to find a plane that has the maximum margin, i.e the maximum distance between data points of both classes. Maximizing the margin distance provides some reinforcement so that future data points can be classified with more confidence.

Support vectors are data points that are closer to the hyperplane and influence the position and orientation of the hyperplane. Using these support vectors, we maximize the margin of the classifier. Deleting the support vectors will change the position of the hyperplane. These are the points that help us build our SVM.

Usually a hyper plane in n dimensional space wil be of n-1 dimension(eg: in 2D space it will be a line and in 3D space it will be a place).

That is why a hyperplace can be represented as: 

$$\large w \bullet x =  w_{n-1}x^{n-1} + w_{n-2}x^{n-2} + ...... +w_2x^2 +  w_1x + w_0 = 0$$

And our goal is to minimize the cost function itteratively and adjust the weights $w$ to get the best fit hyper-plane.

## For Non-Linear Seperable case

The support vector machine is an extension of the support vector classifier that results from enlarging the feature space using **kernels**. The kernel approach is simply an efficient computational approach for accommodating a non-linear boundary between classes.

**A kernel is a function which maps a lower-dimensional data into higher dimensional data.**

There are two ways by which kernel SVM will classify non-linear data.

1. Soft margin
2. Kernel tricks

The points which are the closest to this hyper-plane are called the **support vectors**.

> **The application of the kernel trick is not limited to the SVM algorithm. Any computations involving the dot products (x, y) can utilize the kernel trick.**

### Soft Margin

It allows SVM to make a certain number of mistakes and keep the margin as wide as possible so that other points can still be classified correctly.

*__Degree of Tolerence__*: How much tolerance we want to set when finding the decision boundary is an important hyper-parameter for the SVM (both linear and nonlinear solutions).

### Kernel Trick

The idea is mapping the non-linear separable data from a lower dimension into a higher dimensional space where we can find a hyperplane that can separate the data points. So it is all about finding the mapping function that transforms the ‘n’D input space into a ‘n+1’D output space and to reduce the complexity of finding the mapping function SVM uses Kernel Functions.

**Kernel Functions** are generalized functions that take 2 vectors(of any dimension) as input and output a score(dot product) that denotes how similar the input vectors are. If the dot product is small, vectors are different and if the dot product is large, vectors are more similar.

The reason why it is called as a trick, is because the kernel though theoretically maps a lower dimension vector to a higher dimension vector, but doing so is computaionally highly expensive and afterall we just need the distance between the new vectos and the hyper-plane and not actually the new vectos itself . So the trick here is to not actually map a lower dimensional vector to a higher dimensional vector, but to calulate the similarity between 2 vectors, such a way that it appears to be in higher dimension by showcasing higher or lower similarity.

Thus kernel function takes input the $X$ vector(our dataset set in n dimension) and creates a matrix of shape $n*n$ where any $(i,j)$ pair gives the similarity between data set $i$ a $j$, without actually evaluating the $x_i$ and $x_j$ in $m$ dimensional space and then calculating the similarity.

Mathematically it can be shown as: 

If we have data $x,z \in X$ and a function $\phi: X \rightarrow \R^N$

then kernel function can be defined as $k(x,z) = \langle\phi(x),\phi(z)\rangle$

<img src='../assets/kernel.png' />

Types of Kernel Functions:

1. Linear
2. Polynomial
3. Radial Basis Function(rbf)
4. Sigmoid

#### Radial Bias Function(RBF)

Think of RBF as a transformer/processor to generate new features of higher dimension by measuring the distance between all other data points to a specific dot. The most popular RBF kernel is the Guassian Radial Bias Function.

$\Large k(x_i,x_j) = e^{-\gamma ||x_i - x_j||^2}$

where gamma(𝞬) controls the influence of new features on the decision boundary. Higher the value of 𝞬, more influence of features on the decision boundary. Here gamma is a hyperparameter that can be tuned when using the kernel trick





## Cost function

In SVM we are trying to increase the margin between the hyperplane and the datapoints. So we create our loss function called the **hinge loss** in that way:

$\large c(x,y,f(x)) =\begin{cases} 0, & if\ y*f(x)\geq1 \\ 1 - y*f(x), &else\end{cases}= (1-y*f(x))_+ $

The cost is 0 if the predicted value and the actual value are of the same sign. If they are not, we then calculate the loss value. We also add a regularization parameter the cost function. The objective of the regularization parameter is to balance the margin maximization and loss. The equation after adding the regularization parameter is:

$\Large min_w \lambda ||w||^2 + \sum_{i=1}^{n}(1-y_i\langle x_i,w\rangle)_+$

where n is the no fo examples, $\lambda$ is the regularization parameter and $w$ is weights, i.e. here $f(x) = \langle x_i,w\rangle$

Now we can use the derivative to update our weights:
$\Large \frac{\delta}{\delta w_k}(\lambda ||w||^2) =  2\lambda w_k$

$\Large \frac{\delta}{\delta w_k}(1-y_i\langle x_i, w\rangle )_+ = \begin{cases} 0 & ;y_i\langle x_i,w \rangle \geq 1 \\ -y_ix_{ik} & ;else\end{cases}$

When there is no misclassification, i.e our model correctly predicts the class of our data point, we only have to update the gradient from the regularization parameter.

When there is a misclassification, i.e our model make a mistake on the prediction of the class of our data point, we include the loss along with the regularization parameter to perform gradient update.

$\Large w = \begin{cases}w - \alpha \cdot (2 \lambda w) & ;if \ correct\ classification \\ w + \alpha \cdot (y_i \cdot x - 2 \ lambda w ) &; if\ wrong\ classification \end{cases}$