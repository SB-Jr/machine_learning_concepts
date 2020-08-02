# Population Vs Sample

## Terminology

- *Population*: a set that contains **ALL** members of a group
- *Sample*: a set that contains **some** members of a population (technically a multi-subset of a population)
- *Independent and identically distributed (i.i.d.) random variables*: An assumption that all samples 
  - (a) are **mutually independent**, and 
  - (b) have the same probability distribution.
- *Central limit theorem*: The sampling distribution of i.i.d. random variables tend toward a **normal (Gaussian) distribution** when the sample size is large enough.
- *Expected value*:**Long-run average** **value** of repetitions of the same experiment.
- *Unbiased estimator*: The unbiased estimator’s **expected value** is equal to the true value of the parameter being estimated. In other words, the distributions of unbiased estimators are centred at the correct value. 

## Effect of using a sample space

Given a large Gaussian population distribution with an **unknown** population mean **μ** and population variance **σ²**, we draw **n** i.i.d. samples from the population, such that for each sample **x_i** from a set **X**.

Point to note here is that 

- We dont know the actual $\mu$ and the actual $\sigma$ 
- We dont know the actual size of the population
- We are just considering ‘n’ samples of this population which is considered to be large



$$
\begin{aligned}
x_i \sim \mathcal{N}(\mu, \sigma^2);&\space \forall x_i \in {x_1,x_2,....,x_n}\\
\mu = E[x_i]\\
\sigma^2 = E[(x_i - \mu)^2] &= E[x_i^2] - \mu^2
\end{aligned}
$$



One property to note: For instance, set (1,2,3,4,5) has mean 3 and variance 2. By squaring every element, we get (1,4,9,16,25) with mean 11=3²+2. 

### Estimator

Since we do not know the true population properties, we can try our best to define *estimators* of those properties *from the sample set* using a similar construction.

Let’s put a hat (***^\***) on ***μ\*** and ***σ²\*** and call them ‘pseudo-’ mean and variance, and we define it in the following manner:

$$
\large
\begin{aligned}
\hat \mu & = \frac{1}{n}\sum_{j=1}^n x_j \\
\hat \sigma^2 & = \frac{1}{n}\sum_{j=1}^n(x_j - \hat\mu)^2
\end{aligned}
$$

So basically, the seudo mean is the mean of sample space. And as we can’t achieve a more acurate estimate of the mean of the actual population so we call this the **unbiased population mean estimator**.

So as we cant get the real mean $\mu$ we are substituting it with the $\hat\mu$.

Thus we can say that given the sample space we might never know the true mean of the actual population.

### Bias

And as we have calculated the seudo mean from the sample space, we introduce a bias into ouer calculation, i.e. the pseudo mean is actually biased on the data we have calculated.

eg: We have a die, and we roll it 3 times and get the ouput 1,3 and 6. So our pseduo mean will be 3.33. And based on the our pseudo variance will be 4.22.

But we know that for a die, the true mean is 3.5 and the true variance is 4.25.

So we can see through this example that a bias towards the data was introduced because we only accounted for the sample space and not the population.

So we can conclude here that the pseudo values always underestimate the true values.

## Bessel’s Correction

This states that the true mean is always $\large \frac{n}{n-1}$ times the pseudo mean.

# Reference

https://towardsdatascience.com/why-sample-variance-is-divided-by-n-1-89821b83ef6d

------
