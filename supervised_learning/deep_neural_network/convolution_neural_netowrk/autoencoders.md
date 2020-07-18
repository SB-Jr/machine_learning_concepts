# Autoencoders

## Autoencoders

Autoencoders are a specific type of feedforward neural networks where the input is the same as the output. They compress the input into a lower-dimensional _code_ and then reconstruct the output from this representation. The code is a compact “summary” or “compression” of the input, also called the _latent-space representation._

It has 3 components:

1. Encoder
2. Code
3. Decoder

   The encoder compresses the input and produces the code, the decoder then reconstructs the input only using this code.

![](../../../.gitbook/assets/autoencoder_1.png)

To build an autoencoder we need 3 things: an encoding method, decoding method, and a loss function to compare the output with the target.

> ## Autoencoders are mainly a dimensionality reduction algorithm

### Properties

* Data Specific: Autoencoders are only able to meaningfully compress data similar to what they have been trained on. Since they learn features specific for the given training data, they are different than a standard data compression algorithm like gzip.
* Lossy: The output of the autoencoder will not be exactly the same as the input, it will be a close but degraded representation.
* Unsupervised:  Autoencoders are considered an _unsupervised_ learning technique since they don’t need explicit labels to train on. But to be more precise they are **self-supervised** because they generate their own labels from the training data.

### Architecture

![](../../../.gitbook/assets/autoencoder_2.png)

Both the encoder and decoder are fully-connected feedforward neural networks, Code is a single layer of an ANN with the dimensionality of our choice. The number of nodes in the code layer \(code size\) is a _hyperparameter_ that we set before training the autoencoder.

the autoencoder architecture we’re working on is called a _stacked **autoencoder**_ since the layers are stacked one after another.

**Note: The decoder architecture is the mirror image of the encoder.**

### HyperParameters

There are mainly 4 hyperparameters that we can set before training an autoencoder.

1. **Code\_size**: number of nodes in the middle layer. Smaller size results in more compression.
2. **No of Layers**: the autoencoder can be as deep as we like. 
3. **No of nodes per layer**: The number of nodes per layer decreases with each subsequent layer of the encoder, and increases back in the decoder. Also the decoder is symmetric to the encoder in terms of layer structure. 
4. **Loss Function**: we either use _mean squared error \(mse\)_ or _binary crossentropy_. If the input values are in the range \[0, 1\] then we typically use crossentropy, otherwise we use the mean squared error.

## Sparse Autoencoders

Here we use regularization to encode the data. We can regularize the autoencoder by using a _sparsity constraint_ such that only a fraction of the nodes would have nonzero values, called active nodes.

In particular, we add a penalty term to the loss function such that only a fraction of the nodes become active.

## Use Cases

1. **Data De-noising**: We can train an autoencoder with noise added data i.e. $\(x + noise\)$ and make it predict $x$. This way it will learn how to denoise data and get the useful info out of a data with noise.
2. **Dimensionality Reduction**:  t-SNE is the most commonly used method but struggles with large number of dimensions \(typically above 32\). So autoencoders are used as a preprocessing step to reduce the dimensionality, and this compressed representation is used by t-SNE to visualize the data in 2D space.
3. **Variation Autoencoders\(VAE\)**: VAE learns the parameters of the probability distribution modeling the input data, instead of learning an arbitrary function in the case of vanilla autoencoders. By sampling points from this distribution we can also use the VAE as a generative model. 

