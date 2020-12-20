{% include lib/mathjax.html %}
## Moments of Distribution
Shape of distribution can be explained by only a few moments like _Mean_ and _Variance_. \
The first moment is the mean given by $$ μ_{x} = \sum x.P_{x}= E(X)$$ \
The second moment describes the Variance, which describes how spread out it is around the mean. Second moment is given by $$E(X^{2})$$ \
Thus nth moment is $$E(X^{n})$$

Variance can be given by \
(second moment - square of the first moment) = $$E(X^{2}) - E(X)^{2} = $$E(X^{2}) , if mean is 0.

## Moment-generating function (MGF)

One general  method to describe all the moments is by using Moment generating functions, denoted by $$M_{X}$$\
It maps a random variable X to a function M and is given by , \
$$M_{X} = E[e^{tX}], t\in R $$\
$$e^{tX} = (1+\frac{t}{1!}X+\frac{t^{2}}{2!}X^{2})$$ , by expanding 

$$E(e^{tX}) = E(1+\frac{t}{1!}X+\frac{t^{2}}{2!}X^{2})$$\
$$E(e^{tX}) = (1+E(\frac{t}{1!}X)+E(\frac{t^{2}}{2!}X^{2}))$$
 
If you need to recover the moments, take a derivative and plug in t = 0.

 $$M^{'}(t)=\frac{d}{dt} E[e^{tX}]$$, rest is zero as t=0\
 $$\begin{aligned}
		M^{'}(t) &=\frac{d}{dt} [\sum p(x).e^{tX}] \\
			 &= \sum \frac{d}{dt}p(x).e^{tX} \\
			 &= E(\frac{d}{dt}e^{tX}) = E(X.e^{tX})
\end{aligned} $$
Thus, $$ M^{'}(0) = E[Xe^{0}] = EX$$\
 Second moment\
 $$M^{"}(t) = \frac{d}{dt}M^{'}(t)=\frac{d}{dt} E(X.e^{tX}) = E[X^{2}.e^{tX}] $$\
 $$M^{"}(0) =  E[X^{2}e^{0}] = EX^{2}$$\
 $$n\geq 0 , M^{n}(t) = E[X^{n}.e^{tX}]$$\
 at $$t=0, M^{n}(0) = E[X^{n}]$$
 
Moment-generating function is so named because it can be used to find the moments of the distribution.
 
## MGF of a Normal Distribution:
 
 For a Standard Normal function,$$\mu =0$$ and variance = 1 which is denoted by- N(0,1)\
 $$f(x) = \frac{1}{\sqrt 2 \pi}.e^{\frac{-x^{2}}{2}} $$\
 $$M(t) = e^{\frac{t^{2}}{2}}$$
 
 $$\begin{aligned}
		       M(t) = E(e^{tX}) &= \int_{-\infty}^{\infty} \! e^{tX} f(x)dx \\
					&= \int_{-\infty}^{\infty} \! e^{tX}  \frac{1}{\sqrt 2 \pi}.e^{\frac{-x^{2}}{2}} dx \\
					&= \frac{1}{\sqrt 2 \pi} \int_ \! e^{\frac{-x^{2}-2tx}{2}}dx \\
					&= e^\frac{t^{2}}{2} \frac{1}{\sqrt 2\pi}\int_ \! e^{\frac{-(x-t)^{2}}{2}} dx \\
					&= e^\frac{t^{2}}{2}
   \end{aligned}$$
This is  the integral of the standard normal distribution so $$ \frac{1}{2\pi}\int_ \! e^{\frac{-(x-t)^{2}}{2}} dx $$ integrates to 1. 
 

## Central limit theorem (CLT)

Central limit theorem says that probability distribution of a large sample from a population will be approximately _Normally distributed_, even if the original variables are not normally distributed. It applies to all kind of distribution - discreet, continuous.\
It also allows probability estimation of events even when you do not know the underlying distribution.


Condider $$X^{n} = X_{1},X_{2},X_{3}..$$ are iid with finite mean $$\mu$$ and $$\sigma$$,\
As $$n \to \infty$$, the distribution of  $$\frac{X_{1}+X_{2}+X_{3}.. +X_{3} - n\mu }{\sigma\sqrt n}$$ approaches standard normal N(0,1)

Consider the cumulative distribution of $$Z_{n}$$ , and $$\mu = 0, \sigma = 1 $$\
$$F_{Z_{n}} = P(Z_{n}<x) = P(\frac{X_{1}+X_{2}+X_{3}.. +X_{3} }{\sqrt n} \leq x)$$\
If Z is distributed normal, then $$F(Z_{x}) =  \int_{-\infty}^x \frac{1}{\sqrt 2 \pi}.e^{\frac{-t^{2}}{2}} $$

To prove $$F_{Z_{n}}$$ as $$n \to \infty \! F(Z_{x}) \forall x $$

This can be proved using moment generating functions, 

  $$M_{Z_{n}}(t) \to M(Z_{t})$$  $$\forall t$$
  $$M_{Z_{n}}(t) as n \to \infty =  e^\frac{t^{2}}{2}$$\
  We have \
  $$Z_{n}<x = \sum_{i=1}^n\frac{X_{i}}{\sqrt n}$$
 $$ M\frac{X_{i}}{\sqrt n}(t) = M (\frac{t}{\sqrt n})$$
  $$ M_{Z_{n}}(t)= M (\frac{t}{\sqrt n})^{n}$$
   Let's show that M $$(\frac{t}{\sqrt n})^{n}   n \to \infty e^\frac{t^{2}}{2}$$
   
   $$\lim_{n\to \infty}n.ln M (\frac{t}{\sqrt n}) = \frac{t^{2}}{2}$$
   
  Substituting $$u = \frac{1}{\sqrt n}$$
  
here
		
