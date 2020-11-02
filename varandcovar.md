{% include lib/mathjax.html %}

Listing basic terminologies of Statistics required for Machine Learning.
## Variance
It is the measure of the spread of the data around it’s mean value. 
The variance of a random variable X, with mean $$EX=μ_{x}$$
is defined as  
$$Var(X)=E[(X−μ_{x})^{2}]$$
Larger the variance, the distribution of data is higher.
<p align="center"><img src="img/variance.PNG" width="300px" height="240px"></p>

## Covariance
It gives the relationship between two variables X and Y. It tells us how the data is spread relative to each other.

The covariance between X and Y is defined as
$$Cov(X,Y)=E[(X−E(X))(Y−E(Y))]=E[XY]−(E(X))(E(Y))$$
$$Cov(X,Y)=E[(X−μ_{x})(Y−μ_{y})]=E[XY]−μ_{x}μ_{y}$$

If they are centered around the mean, then second component is zero
$$Cov(X,Y) = E(XY)$$

By normalising the covariance, we get Correlation Coefficient given by :

Pearson’s coeff $$ρ(x,y)= Cov(X,Y)/σ_{x}σ_{y}$$

Positive correlation occurs when variables move in the same direction; if one variable increases the other variable also increases.

When one variable increases and the other decreases, then there is negative correlation.

<p align="center"><img src="img/covar.PNG" width="600px" height="240px"></p>

## Covariance matrix 
It is a square matrix  indicating the covariance between each pair of elements of vector. Diagonal elements consist of variances, and off diagonal elements will have covariances.
The covariance matrix is symmetric and positive semi definite.

Covariance matrix denoted by Σ is defined by
$$Cov(X)=E(XX^{T})−μμ^{T}$$ 

If mean is zero,
$$Cov(X)=XX^{T}/n$$



