# Fundamentals

## Maths Fundamentals used in ML

## Notations

| Notation | Meaning |  |  |  |  |
| :--- | :--- | :--- | :--- | :--- | :--- |
| $a$ | small letters are used to denote scalar |  |  |  |  |
| $A$ | capital letters are used to denote vectors |  |  |  |  |
| $f: \mathbb{A} \rightarrow \mathbb{B}$ | A relation with domain $\mathbb{A}$ and range $\mathbb{B}$ |  |  |  |  |
| $\langle x,y \rangle$ | Denotes the dot product between x and y |  |  |  |  |
| $f\(x,\theta\)$ | A function of x, parameterized by $\theta$ |  |  |  |  |
| $\sigma\(x\)$ | Logistic sigmoid of x i.e. $\Large \frac{1}{\(1 + e^{-x}\)}$ |  |  |  |  |
| $ |  | x |  | \_P$ | $L^P$ norm of x |
| $ |  | x |  | $ | $L^2$ norm of x |
| $f'\(a\) = \frac{df}{dx}\(a\)$ | Derivative of $f\(x\)$  with respect to $x$ at input $a$ |  |  |  |  |
| $\frac{\delta f}{\delta x\_i}\(a\)$ | Partial derivative of $f\(x\)$ with respect to $x\_i$ at input $a$ |  |  |  |  |
| $\triangledown f\(a\) \in \mathbb{R}^n $ | Gradient of $f:\mathbb{R}^n \rightarrow \mathbb{R}$ at input $a$ |  |  |  |  |
| $\triangledown f\(A\) \in \mathbb{R}^{m\*n}$ | Matrix darivative of $f:\mathbb{R}^{m\*n} \rightarrow \mathbb{R}$ at input $A$ |  |  |  |  |
| $J\(f\)\(a\) \in \mathbb{R}^{m\*n}$ | Jacobian matrix of $f:\mathbb{R}^n \rightarrow \mathbb{R}^m$ |  |  |  |  |
| $H\(f\)\(a\) = \triangledown^2f\(a\) \in \mathbb{R}^{n\*n}$ | Hessian matrix of $f:\mathbb{R}^n \rightarrow \mathbb{R}$ at input $a$ |  |  |  |  |
| $a \perp b $ | Random variables $a$ and $b$ are independent |  |  |  |  |
| $\mathcal{N}\(\mu, \Sigma\)$ | A gussian distribution with mean $\mu$ and covariance matrix $\Sigma$ |  |  |  |  |
| $x \sim P\(\theta\)$ | Random variable $x$ has distribution $P$ |  |  |  |  |
| $E\_{x \sim P}\[f\(x\)\]$ | Expectation of $f\(x\)$ with respect to $P$ |  |  |  |  |

