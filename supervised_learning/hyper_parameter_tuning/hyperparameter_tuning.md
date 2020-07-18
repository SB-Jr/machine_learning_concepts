# HyperParameter\_tuning

## Hyperparameter Tuning

The hyper-parameter optimization algorithms can be separated into **three main categories**, namely

* exhaustive search of the space, 
* surrogate models and 
* finally some algorithms mixing some ideas of the two previous categories and specifically dedicated to hyper-parameters tuning.

For all these algorithms, a search space has to be defined beforehand, setting bounds for all the hyper-parameters, and also adding some prior knowledge on them \(like setting a non-uniform distribution for the search, e.g. learning rates have to be searched on a log distribution\).

### Exhaustive Search of Space

* **Grid Search**: When we can provide the hyper parameters in decrete form we can use the Grid Search algorithm. It is basically a _parallel problem_ and one needs a lot of computing power to train several models in parallel. It also suffers from the _curse of dimensionality_, i.e. no of configuration to try is exponential with regards to teh no of hyper-parameter to be optimized.
* **Random Search**: It randomly samples the search space instead of discretizing it with a Cartesian grid. But as it is a random algorithm, it has no end, so we need to provide a _time budget_. This algorithm also suffers from the _curse of dimensionality_. The only advantage we have here over Grid Search is that if any 2 hyper-parameters are correlated, it will easily find the optimal parameters.

Random search and grid search are an attractive first option for optimization. They are very easy to code, can be run in parallel and they do not need any form of tuning.

Their drawback is that there is no guarantee of finding a local minimum to some precision except if the search space is thoroughly sampled.

If the model takes a significant time to run using a lot of computational resources, random or grid search are inefficient as they do not use the information gained by all the previous tries.

### Surrogate model

A surrogate model of the validation loss as a function of the hyper-parameters can be fit to the previous tries, and tell where the local minimum might be. These methods are called **Sequential Model-Based Optimization \(SMBO\)**.

* **Bayesian Optimization**: 
* **Tree-Structured Przen estimators \(TPE\)**: This method handles categorical hyper-parameters in a tree-structured fashion. One of the great drawback of tree-structured Parzen estimators is that they do not model interactions between the hyper-parameters. 

### Dedicated HyperParameter Tuning Algorithms

The two following methods \(Hyperband and PBT\) introduce a form of early stopping for bad runs. For all the previous methods, each learning has to be run until the end.

* **Hyperband**: Hyperband is a variation of random search, but with some [explore-exploit](https://en.wikipedia.org/wiki/Multi-armed_bandit#Empirical_motivation) theory to find the best time allocation for each of the configurations.

  > This algorithm suffers from what is called the _“n vs B/n”_ trade-off, i.e. for a given budget\(B\), it is not clear whether to search for many configurations \(large _n_\) for a small time, or explore few configurations but allocating a lot of resources to them \(large _B/n_\)

* **PBT \(Population based training\)**: Population-based training mixes ideas from genetic optimization algorithms during the SGD optimization steps. The learning of the ML model is seen as a dynamical system where hyper-parameters are to be chosen every _p_ time steps.
* **Fabolas**: This stands for **FA**st **B**ayesian **O**ptimazation for **LA**rge data**S**ets. It tries to increase the speed of Bayesian optimization by learning the ML model on a sampled dataset \(but evaluating its performance on the full validation dataset\). The idea is that a small portion of the data \(less than 10 %\) is sufficient to check if a hyper-parameter combination is promising or not.
* **BOHB \(Bayesian Optimization and HyperBand\)**: mixes the Hyperband algorithm and Bayesian optimization. It uses Hyperband to determine how many configurations to try within a budget but instead of randomly sampling them, it uses a Bayesian optimizer \(using a Parzen estimator with no tree structure\). **It is also parallel \(as Hyperband\) which overcomes a strong short-coming of Bayesian optimization.**

## Conclusion

Choosing the right hyper-parameter optimization algorithm depends on the ML problem, the computing infrastructure and the associated computing budget, etc.

* _A random search_ might be sufficient if the ML model is very simple and can be run fast, but it will not be efficient enough for large scale ML models. 
* Using _Hyperband_ \(or its associated algorithm _BOHB_\) means that the ML model can be checkpointed during training. 
* _PBT_ aims at finding an optimal training schedule rather than optimizing the hyper-parameters.

