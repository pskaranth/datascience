{% include lib/mathjax.html %}

## Optimization Algotrithms

Sigmoid Neuron is given by:

$$ y = \frac{1}{e^{-\omega x+b}} $$

The optimum value of w and b are chosen such that squared error loss is miminized. \
This is done using an optimization algorithm called _Gradient descent algoritm_. Objective is to find the local minimum of a function.

## Gradient Descent Algorithm

Let's denote loss function (Loss with respect to $$\omega$$ and b) as follows :

$$ L(\omega,b) =  L(\theta) $$
 
New loss is less than the old loss and denoting $$ \Delta \theta $$ = u
 
$$L(\theta + \eta u) -  L(\theta) < 0 $$
 
Using Taylor series:
 
$$L(\theta + \eta u ) = L(\theta) + \eta * u^{T} \nabla_{\theta} L(\theta)$$
 
$$L(\theta + \eta u ) - L(\theta) = \eta * u^{T} \nabla_{\theta} L(\theta)$$
 
 From the previous equation, this would work only if:
 
 $$u^{T} \nabla_{\theta} L(\theta)<0 $$
 
This can be negative if the cos of angle between $$u^{T}$$ and $$\nabla $$ is equal to -1 , which means they are 180 degrees apart.

This also means that we should choose the direction of the vector opposite to the gradient vector.

Thus parameter update rule can be given by:

$$ \omega_{t+1} = \omega_{t} -\eta \Delta \omega_{t}$$

$$ b_{t+1} = b_{t}-\eta \Delta b_{t}$$

where $$\Delta \omega_{t} = \frac{\partial L(\omega,b)}{\partial \omega}$$

and $$ \Delta b_{t} = \frac{\partial L(\omega,b)}{\partial b} $$

If squared error loss is considered, then 
$$L(\theta) = \sum_{i=1}^n min||y_{i}-f(x_{i})||^{2} $$

$$\frac{\partial L(\omega,b)}{\partial \omega}  = \frac{\partial \sum_{i=1}^nmin||y_{i}-f(x_{i})||^{2}}{\partial \omega} $$

$$\begin{aligned}
\frac{\partial \sum_{i=1}^nmin||y_{i}-f(x_{i})||^{2}}{\partial \omega} &= (y - f(x))\frac{\partial}{\partial \omega}(f(x))\\
																	   &= (y - f(x))\frac{\partial}{\partial \omega}(\frac {1}{1+e^{-(\omegax+b)}}) \\
																	   &= (y - f(x))*(f(x)(1-f(x)x)\\
\end{aligned}
$$

If Cross entropy loss is considered, then

$$L(\theta) = -[(1-y)log(1-\hat{y})+ylog\hat{y}]$$

$$ \frac{\partial L(\omega,b)}{\partial \omega}  = \frac{\partial L(\theta)}{\partial \hat{y}} \frac{\partial \hat{y}} {\partial \omega} $$ 

$$\begin{aligned}
\frac{\partial L(\theta)}{\partial \hat{y}} &= \frac{\partial (-((1-y)log(1-\hat{y})+ylog\hat{y}))}{\partial \hat{y}} \\
											&= \frac{\hat{y}-y}{(1-\hat{y})\hat{y}} \\
\frac{\partial \hat{y} }{\partial \omega} 	&= \frac{\partial}{\partial \omega} (\frac {1}{1+e^{-(\omega x+b)}}) \\	
										    &= \hat{y} (1- \hat{y}) x\\
\end{aligned}
$$

Combining both,
$$ \frac{\partial L(\theta)}{\partial \omega} = (\hat{y}-y) x$$	

The gradient descent update rule might take longer time as the rate at which the function is minimized totally depends on the slope. At certain points, it may navigate the slope very slowly to reach the local minima.

In order to make gradient descent effective, there are lot of different ways of implementation.

## Momentum Based Gradient Descent

This version of gradient descent rule takes larger values of updates to reach the local minimum and hence it will be faster than the vanilla gradient descent.

We have gradient descent update rule as :
$$ \omega_{t+1} = \omega_{t} -\eta \Delta \omega_{t}$$

In case of momentum based gradient descent rule :\
$$v_{t} = \gamma * v_{t-1} + \eta \Delta \omega_{t}$$
$$ \omega_{t+1} = \omega_{t} - v_{t}$$

$$\begin{aligned}
v_{0} &=  0 \\
v_{1} &=  \gamma * v_{0} + \eta \Delta \omega_{1} = \eta \Delta \omega_{1} \\
v_{2} &=  \gamma * v_{1} + \eta \Delta \omega_{2} = \gamma. \eta \Delta \omega_{1}  + \eta \Delta \omega_{2} \\
v_{3} & = \gamma * v_{2} + \eta \Delta \omega_{3} = \gamma(\gamma. \eta \Delta \omega_{1}  + \eta \Delta \omega_{2}) +  \eta \Delta \omega_{3}\\
      & = \gamma * v_{2} + \eta \Delta \omega_{3} = \gamma^{2}. \eta \Delta \omega_{1} + \gamma  \eta \Delta \omega_{2} + \eta \Delta \omega_{3}\\
v_{t} &=  \gamma * v_{t-1} + \eta \Delta \omega_{t} = \gamma^{t-1}. \eta \Delta \omega_{1} + \gamma^{t-2}  \eta \Delta \omega_{2} + \eta \Delta \omega_{t}\\

\end{aligned}
$$

Instead of considering just the current gradient, it takes it account the exponential decaying weightage of all the previous gradients. Because it navigates faster, sometimes it might miss converging and it takes various oscillations to achieve the goal.

## Nesterov Accelerated Gradient Descent 

In case of this version, 

$$\omega_{temp} = \omega_{t} -\gamma v_{t-1} $$

$$\omega_{t+1} = \omega_{temp} -\eta \Delta \omega_{temp} $$

$$ v_{t} = \gamma v_{t-1} +\eta \Delta \omega_{temp}$$

Using the history we compute the weight $$\omega_{temp} $$ and use it to compute further value of weights.\
In this case the oscillations are much smaller compared to the above  gradient descent algorithms.

Many features in the real worls are sparse.. Hence it would require higher learning rate for the features which are non-zero so that it has more effects on the weights. For dense features, learning rate needs to be small. Below algorithms accommodate this change and have adaptive based learning rate.

## Adagrad 

In Adagrad, if there are frequent updates for a parameter, a smaller learning rate is introduced. But for a parameter with less frequency of updates, larger learning rate is used. 
This is achieved by having a learning rate divided by history of updates.

$$ v_{t} = v_{t-1} + (\Delta \omega)^{2} $$
$$ \omega_{t+1} = \omega_{t} -\frac{\eta}{\sqrt{v_{t}}+\epsilon} \Delta \omega  $$

For a parameter with frequent updates it might so happen that after a while it might stop updating $$\omega $$ and b  as the learning rate gets reduced. So the function reaches close to minima but may not converge as expected. 

## RMS Prop

In this case, the learning rate is reduced at a much lower rate as compared to Adagrad.\
There is an exponential decaying sum of derivatives for the history component.

$$ v_{t} =\beta v_{t-1} + (1- \beta)(\Delta \omega)^{2} $$\
$$ \omega_{t+1} = \omega_{t} -\frac{\eta}{\sqrt{v_{t}}+\epsilon} \Delta \omega  $$

## Adam 

Adam algorithm combines the idea of both Momentum based and RMS Prop.   

$$ m_{t} =\beta v_{t-1} + (1- \beta)(\Delta \omega) $$\
$$ v_{t} =\beta v_{t-1} + (1- \beta)(\Delta \omega)^{2} $$\
$$ \omega_{t+1} = \omega_{t} -\frac{\eta}{\sqrt{v_{t}}+\epsilon} m_{t}  $$

It ensures that updating of weights considers the history of derivatives ($$m_{t}$$) and also makes sure that learning rate is adaptive.

When there are over million data points, it becomes computationally intensive to update weights after computing partial derivative and accumulating gradients for each of the points. There are different strategies that can be used with various algorithms stated above.


## Batch based gradient descent

We look at all the data, we compute the partial derivative of the loss function for every data point, then we take the sum and make the updates of parameters. Number of steps in one epoch is 1.

## Mini-Batch based gradient descent

In case of mini-batch, we look at the data(N) in batches of size B. Partial derivatives are computed and accumulated for every batch size. The weight and bias are updated after the iteration runs for B times. Batch size chosen are 32, 64, 128.. Number of steps in one epoch is N/B.

## Stochastic based gradient descent

In the case of Stochastic, we look at one data point, compute the derivative and update the parameters. This is same as mini batch with batch size 1. Number of steps in one epoch is N.

The downside of using mini-batch or stochastic, the true derivative is not computed because the true loss is the total loss over all the data points. The gradient would be the sum of the partial derivatives with respect to all the data points.

References:
* DeepLearning - Padhai OneFourthLabs
