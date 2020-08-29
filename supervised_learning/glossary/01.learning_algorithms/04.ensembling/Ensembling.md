# Ensembling

An Ensemble method is a technique that **combines the predictions from multiple machine learning algorithms** together to make more accurate predictions than any individual model. A model comprised of many models is called an **Ensemble model**.

<img src='../../assets/ensembling.png'/>

> *A good ensemble contains high performing models which are less correlated.*



# Types of Ensembling Learning

## Rank or Bagging Ensembling 

Involves combining the predictions of various models on the test set. This is the most basic and convenient way to ensemble as the original models do not need to be retrained.

## Stacking

Was introduced by Wolpert in a [1992 paper](http://www.researchgate.net/profile/David_Wolpert/publication/222467943_Stacked_generalization/links/0c960529e2b49a95f2000000.pdf), 2 years before the seminal Breiman paper “[Bagging Predictors](http://statistics.berkeley.edu/sites/default/files/tech-reports/421.pdf)”. The basic idea here is to user a pool of base predictors, and then use another predictor to combine the base predictions. This technique was popularized by the [Netflix Prize competition](http://www.netflixprize.com/leaderboard.html).

## Blending

Very similar to stacking but requires a small holdout set (say 10%) of the train set. The stacker model then trains on this holdout set only.



Very roughly, we can say that bagging will mainly focus at getting an ensemble model with less variance than its components whereas boosting and stacking will mainly try to produce strong models less biased than their components (even if variance can also be reduced).



# Techniques

## Ranking Techniques

### Voting

When you have a good collection of large well performing models, implementing a voting ensemble works well.

### Averaging

Works well on a wide range of problems and metrics (AUC, MSE, LogLoss). Here, an average of predictions from all base models is used to make a final prediction. 

### Rank Averaging

Similar to averaging, but instead of giving every model an equal weight, using a normalized validation score of all the models as a weight can help improve generalization.

### Historical Averaging

rank averaging requires a validation set. However, if you only want to predict for a single new sample, a solution could be to use historical ranks. This involves storing old test set predictions together with their rank. Hence, when you want to make a new prediction, you find the closest old prediction and take its historical rank.



## Stacking Techniques

### Feature weighted linear Stacking

 This stacks engineered meta-features together with model predictions. The idea here is that the stacking model learns which base model is the best predictor for samples with a certain feature value. 

### Quadratic weighted Stacking

This is similar to the feature weighted linear stacking method, but it creates non-linear combination of model predictions as features for the second stage model.

### StackNet

This meta-modelling framework resembles a feedforward neural network and uses Wolpert’s stacked generalization on multiple levels. However, rather than being trained through back propagation, like a traditional neural network, StackNet is built iteratively one layer at a time (using stacked generalization), each of which uses the final target as its target. 



# Pitfalls of Ensembling

- Exponentially increasing training times and computational requirements. This greatly reduces iteration time and ultimately the number of experiments you can run.
- Increased demand on infrastructure to maintain and update these models.
- Greater chance of data leakage between models and/or stages in the ensemble.