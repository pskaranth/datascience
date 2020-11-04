{% include lib/mathjax.html %}
## Principal Component Analysis(PCA)

PCA is the Dimensionality Reduction method that is used to reduce the number of features/dimensions in a high dimensional space and yet retaining the important information.

Benefits of reducing number of features:
- Reduces the amount of storage required.
- Removes noise and irrelevant information.
- It is done to achieve better fitting of the predictive model.

How is it done?
Projecting the high dimensional data to a lower dimensional subspace thereby retaining the points which have higher variance and ignoring the points which have low variance.
Projections which have the largest variance is the first principal component, second largest is the second principal component and so on.

Consider a 2 dimensional data set below with $$x_{1}$$ and $$x_{2}$$ features. The goal is to reduce the dimension from 2D to 1 D.
We project points onto the line by finding the closest points on the line. We replace the point by the length of the line(projection).
<p align="center"><img src="img/KNN.png" width="300px" height="240px"></p>
The 2D points are replaced by the length of line shown in blue. The direction of the line is the direction of the _maximum variance_.

Projection of x onto unit vector u is given by 
$$x.u = u.x = u^{T}x $$

Variance of  x in the direction u is given by $$Σ(x.u)^{2}$$

$$Var = Σ(x.u)^{2}$$

In matrix form this is given as: 

$$
\sigma^{2} = \frac{(xu)^{T}(xu)}{n}\\
    = \frac{u^{T}x^{T}xu}{n}\\ 
    = u^{T}\frac{x^{T}x}{n} u\\
    = u^{T} Σ u\\
$$

where  Σ is the covariance matrix $$\frac{x^{T}x}{n} $$ considering mean is zero.

Thus variance given by $$u^{T}Σu$$ should be maximised such that only highest variance is considered.

By introducing a new variable, Lagrange multiplier $$\lambda$$ and adding constraint in the equation ($$u.u^{T} = 1 $$) , we get:

$$
L(u,\lambda) = \sigma^{2}- \lambda(u.u^{T}-1)\\
\frac{dL}{d\lambda} = u.u^{T}-1\\
\frac{dL}{du} = 2 Σ u - 2\lambda.u\\
$$

Setting the derivatives to zero for maximising:
$$
u.u^{T} = 1\\
M.u = \lambda.w\\
$$

Desired vector u is an Eigen vector of the covariance matrix M and the maximising vector will be associated with largest Eigen value $$\lambda$$


