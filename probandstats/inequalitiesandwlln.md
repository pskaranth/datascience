{% include lib/mathjax.html %}
## Markov's Inequality
 
Let's look at this example to get the intuition of Markov's inequality.
 
If average height of Meerkats is 10 inches, can half of Meerkats be greater than 40 inches ? \\
Then overall average will be 1/2 *40 = 20 inches which is > 10 (even if rest of the Meerkat's height is zero)

So if any fraction(F) * 40 >10, average would be greater than 10.
To maintain the average at 10, $$
								F*40<10 
								F*(4*10)<10
								F*(4*\mu)<\mu
								F_{4.\mu}<1/4
								$$
Probability that X is bigger than $$4\mu$$ is less than or equal to 1/4
								
This can be generalised into    $$P(X\geq\alpha\mu)<= 1/\alpha$$

The more direct form is $$  \forall a\geq \mu,  P(X\geq a)\leq\frac{\mu}{a}$$

$$\mu = \sum_{x}^x.p(x) $$
\geq \sum_{x\geqa}^x.p(x) $$
\geq \sum_{x\geq a}^a.p(x) $$
= a.P(X\geq a)

In Markov's inequality, Probability that any X is $$\alpha$$ times bigger than its mean is atmost 1/\alpha$$
In Chebyshev's inequality, Probability that any X is $$\alpha$$ times further away from $$\mu$$ than \sigma is 1/(\alpha^{2})

## Chebyshev's Inequality

This is given by :
$$\forall \alpha>=1 P(|X- \mu|\geq\alpha\sigma ) <= \frac{1}{(\alpha^{2})}$$

This can also be given by
$$\forall a\geq\sigma P(|X- \mu|\geq a ) <= \frac{(\sigma^{2})}{(\a^{2})}$$

For any random variable X,
$$ \mu_{x} = E(X)      \sigma^{2}= V(X) = E(X- \mu_{x})^{2} $$
Let $$ Y = (X- \mu_{x})^{2}  , Y\geq0 , \mu_{y} = E(X- \mu_{x})^{2} = \sigma^{2} $$

$$P(|X-\mu_{x}|)\geq\alpha) = P((|X-\mu_{x}|)^{2}>a^{2})$$
$$= P(Y\geq a^{2})\leq \frac{\mu_{y}}{a^{2}}$$ applying Markov's inequality
$$= \frac{\sigma_{x}^{2}}{a^{2}}$$

## Weak Law of Large Numbers 

Independent Identically Distributed(iid): Independent random variables with same distribution

As size of the sample grows larger, sample mean converges to population mean.

Condider $$X^{n} = X^{1},X^{2},X^{3}..$$ are iid with mean $$\mu$$ and $$\sigma$$ , Sample mean is given by $$\bar{X^{n}}= \frac{\sum(X_{i})}{n}$$
Expectaion 
$$E(\bar{X^{n}}) = E(\frac{\sum(X_{i})}{n})  = \frac{1}{n}\sum(E(X_{i})) =\frac{1}{n}\sum(\mu)=\mu $$
Variance
$$V(\bar{X^{n}}) = V(\frac{\sum(X_{i})}{n})  = \frac{1}{n^{2}}\sum(V(X_{i})) =\frac{1}{n^{2}}\sum(\sigma^{2})=\frac{1}{n}\sum(\sigma^{2}) $$
By Chebyshev's inequality,
$$forall \epsilon>0, P(|\bar(X^{n})-\mu|\geq\epsilon)\leq \frac{1}{n.\epsilon^{2}}\sum(\sigma^{2}) $$
As n approaches to infinity, RHS will be 0.
