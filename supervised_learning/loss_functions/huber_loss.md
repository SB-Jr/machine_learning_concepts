# Huber Loss

## aka Smooth Mean Absolute Error



## Mathematical Formula

$$\LARGE L_{\delta}(y, f(x)) = \begin{cases}& \frac{1}{2}(y - f(x))^2 & for\ |y-f(x)|\leq \delta \\
& \delta|y-f(x)|-\frac{1}{2}\delta^2 & otherwise
\end{cases}$$



## Explanation

Huber loss function is defined as the combination of MSE and MAE Loss function as it approaches **MSE when 𝛿 ~ 0 and MAE when 𝛿 ~ ∞ (large numbers)**. It’s Mean Absolute Error, that becomes quadratic when the error is small. And to make the error quadratic depends on how small that error could be which is controlled by a hyperparameter, 𝛿 (delta), which can be tuned.

The choice of the delta value is critical because it determines what you’re willing to consider as an outlier. Hence, the Huber Loss function could be less sensitive to outliers compared to MSE Loss function depending upon the hyperparameter value. Therefore, ***it can be used if the data is prone to outliers and we might need to train hyperparameter delta which is an iterative process.***

<img src='../assets/huber_loss.png' />