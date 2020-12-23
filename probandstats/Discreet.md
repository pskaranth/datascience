## Probability Distribution
(_From Wiki_) It is the mathematical function which gives the probabilities of occurrence of different possible outcomes for an experiment.
		  
## Discrete Probability Distribution
It is a probability distribution that can take on countable number, finite or countably-infinite number of discrete values. For example throwing  a dice or tossing a coin.

## Bernoulli Distribution
It is the distribution which takes values 1 with probability p and 0 with probability (1-p) = q.

Expectation
$$E(X)  = p.1 +(1-p).0 = p$$
Variance 
$$V(X) = E(X^{2}) - (E(X))^{2} $$
We evaluate $$E(X^{2}) = p.1^{2} - (1-p).0^{2}  = p$$
$$V(X) = p - p^{2} = p(1-p) = pq$$

## Binomial Distribution
Distribution of n number of experiments with number of successes(k), probability p and number of failures (n-k) with probability (1-p).\
Each sequence has probability $$p^{k}.q^{n-k}$$\
Nmmber of such sequence is given by $$\binom n,k$$\
Hence the over all distribution can be given by $$b_{p,n}k= \binom n,k p^{k}.q^{n-k}$$\

Expectation \
X is a binomially distributed variable,\
$$E[X] = E[X_{1}+X_{2}+...] = E[X_{1}]+E[X_{2}]+.. = p+p...+p =np$$\
Since X is sum of identical Binomial variables.

Variance\
V(X) = np(1-p)

Applications include :\
Probability of Rainy Days in a month\
Positive Reponse to a  treatement.\

## Poisson Distribution
It is a discrete probabiity distribution that gives the probability of given number of events occurring in a fixed interval of time or space.\
This event occurs with a known constant mean rate and independent of the time since last event.

Probability Distribution can be given by \
$$P_{\lamda}k = e^{-\lambda}. \frac{\lambda ^{k}}{k!}$$
$$\lambda$$ the parameter\
e is Euler's number (e = 2.718)\
k is the number of occurrences\


Approximates Binomial $$B_{p,n}$$ for large n and small p so that $$np = \lambda$$

$$b_{p,n}k= \binom n,k p^{k}.(1-p)^{n-k}$$
Let p= \frac{\lambda}{n}$$
$$\begin{aligned}
b_{p,n}k &=\binom n,k (\frac{\lambda}{n})^{k}(1-\frac{\lambda}{n})^n-k \\
&= \frac{n\_{k}\qquad}{k!} .\frac{\lambda^{k}}{n^{k}}.\frac{1-\frac{\lambda}{n}}^n{1-\frac{\lambda}{n}}^k \\
&= e^{-\lambda}\frac{\lambda^{k}}{k!}\\
\end{aligned}$$
rest of the parameters will be equal to 1\
and $$\frac{1-\frac{\lambda}{n}}^n =(({1-\frac{\lambda}{n}})^\frac{n}{\lambda})^\lambda = (e^{-1})^{\lambda}$$

Expectation \
$$E(X) = \lambda$$

Variance \ 
$$E(X)(X-1) = \lambda^{2}$$

Applications include:
People clicking ads.
Daily store customers..

## Geometric Distribution

It gives the probability that the first occurrence of success requires n independent trials, each with success probability p and failure with probabiity q=(1-p). Probability of nth trial being successful can be given by
$$g_{p}(n) = q^{n-1}.p$$

Expectation \
$$E(X) = \frac{1}{p}$$

Variance \
$$V(X) = \frac{q}{p^{2}}$$

Geometric Distribution have memoryless property. After n number of events, any new(m) event behaves as if it's from the start.
$$P(X=n+m| X>n) = P(X=m)$$

$$\begin{aligned}
P(X=n+m| X>n) &= \frac{P(X=n+m, X>n)}{P(X>n)}\\
&= \frac{P(X=n+m)}{P(X>n)}\\
&= \frac{p.q^{n+m-1}}{q^{n}}\\
&= p.q^{m-1}\\
&=P(X=m)\\
\end{aligned}
$$
