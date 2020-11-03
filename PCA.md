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

Consider a 2 dimensional data set below with x1 and x2 features. The goal is to reduce the dimension from 2D to 1 D.
We project points onto the line by finding the closest points on the line. We replace the point by the length of the line(projection).

Projection of x onto unit vector u is given by 
$$x.u = u.x = u^{T}x $$
Variance of  x in the direction u is given by $$Σ(x.u)^{2}$$

$$Var = Σ(x.u)^{2}$$

In matrix form this is given as: 
$$= \frac{(xu)^{T}(xu)}{n}$$
$$= \frac{u^{T}x^{T}xu}{n} $$
$$= u^{T}\frac{x^{T}x}{n} u $$
$$= u^{T} Σ u $$
Thus variance is given by $$u^{T}Σu$$

