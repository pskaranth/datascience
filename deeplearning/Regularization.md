{% include lib/mathjax.html %}

## Regularization

In general in deep neural netwoks, there is high variance (low training error and high vaidation error). High variance leads to overfitting. To reduce overfitting in deep neural networks we use _Regularization_.

## L2- Regularization

It ensures that the training error is not zero, because that implies that the validation error is very high.\
So the idea is to add a parameter to make sure the training error does not reach zero. In L2 norm, the parameter is the sum of square of weights. 

With L2 norm, the goal is to minimize training error and also the sum of the square of weights. Also since higher value of weights causes non-linearity in the system.

$$min L(\theta) = L_{train} \theta + \Omega(\theta) $$
$$ \theta = [W_{111}, W_{112},..] $$\
$$ \Omega(\theta) = ||\theta||^{2} = W_{111}^{2} +W_{112}^{2}+...$$\
$$\Delta W_{ijk} = \frac{\partial L(\theta)}{partial W_{ijk}}$$ \
$$\Delta W_{ijk} = \frac{\partial L_{train}(\theta)}{partial W_{ijk}} +\frac{\partial \Omega(\theta)}{partial W_{ijk}} $$

$$\frac{\partial \Omega(\theta)}{partial W_{ijk}} = 2W_{ijk}$$

## Data Augmentation

When there are too many parameters than the data, it is easy to drive the training error to zero. Augmenting the model with more data will not cause the training error to zero. 

## Early stopping 

A patience parameter denoted by p is set. This is the number of epochs where the model can wait and check if the validation error decreases any further. If it does not, we return the model parameters at the last minimum validation error.

## Batch Normalization

Activation function (_h_)  acts as inputs to the next layer of neural network. It makes sense to normalize these values just like normalizing inputs(x).\
$$\mu_{j} = \frac{1}{m}\Sigma h_{ij}$$ and \
$$\sigma_{j} = \sqrt(\frac{1}{m}\Sigma(h_{ij}-\my_{j})^{2})$$ are computed in every batch where m is the batch size.

$$h_{ij}norm  = \frac{h_{ij}-\mu_{j}}{\sigma_{j}}$$\
$$ h_{ij}^{final} = \gamma_{j} h_{ij}^{norm}+\beta_{j}$$

\gamma and \beta are learned along with other parameters of the network.
Model has the fliexibility to learn, that is if normalization helps, then have (based on the equation it is equivalent to $$\sigma_{j}$$) $$\gamma_{j} = 1 $$and ($$\mu_{j} = 0 $$)\beta_{j} = 0$$\$$.

* Normalize activation functions ($$h_{j}$$).
* Allow the flexibility of learning $\gamma$$ and $$\beta$$ . Have appropriate $$\sigma$$ and $$\mu$$ such that over all loss decreases.

How does it act as a _Regularizer_?
$$\sigma_{j}}$$ and $$\mu_{j}$$ are computed from a mini batch. They contribute towards the noise as they are not computed from the entire data.
Whenever noise is introduced that leads to better regularization.

## Dropout

Random neurons are dropped out from the network to avoid overfitting. \
If there are n nodes in neural network, then each of nodes have the flexibility to remain or drop out, then the total number of ways we can design the network is $$2^{n}$$ .. The overall network is thinned out because of severl neurons are dropped out.

* Parameters are shared across entire network.
* At each iteration for every batch, nodes are dropped out from the network randomly and parameters are learned. Parameters are passed on to the second iteration and so on.
* At training time, each node in the network is associated with probability p and this decides if the neuron is going to be retained.
* At test time, weights are multiplied with p times ($$wp_{1},wp_{2}$$)
* Prevents co-adaptation as rest of the neurons have to compensate for learning.
* It again acts as a regularizer by introducing noise to the network. 

References:

* DeepLearning - Padhai OneFourthLabs
