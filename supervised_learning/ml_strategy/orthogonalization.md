# Orthogonalization

Orthogonalization is a system design property that ensures that modification of an instruction or an algorithm component does not create or propagate side effects to other system components. Orthogonalization makes it easier to independently verify the algorithms, thus reducing the time required for testing and development.

## Scenarios

### Bad result on Training set

* Bigger Network in case of deep learning
* Different Optimization algorithm

### Good on Training Set but not on Validation Set

* Regularization
* Bigger Training set

### Good on Validation set but not on Test set

* Bigger Validation set
* Changing cost function

### Bad result on Real world test

* Changing cost function

