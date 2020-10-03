{% include lib/mathjax.html %}
 
# Generative Modeling

There are two kinds of modelling in machine learning.
For the below explanations, consider x = features and y = labels or classes.

### Discriminative Modeling:
Predicting y based on x by learning a function that takes input as x and outputs y. It maps directly the input labels x to the class labels y by way of  discriminating x between different classes but have no idea about how the data is generated.

### Generative Modeling:
To get an idea how the data is generated, and learn a function that gives a score to the configuration determined by x and y together.
For any new point x, output y is predicted based on the label which has the largest joint distribution.
Why do we pick y with the largest joint distribution?

This is because of the direct consequence of Bayes’ rule. Based on this rule, we pick a label which is most likely to occur with given x inputs.
Probability that the label is j given x is given by 

$$ P(y=j/x)= \frac{P(y=j)P(x/y=j)} {P(x)}$$
                                       
Since P(x) is not dependent on j, the denominator can be excluded. We will pick the label which maximises the above equation.
Maximising the equation would also mean we are closer to the mean where density is high.

### Steps to follow when predicint using Gaussian Generative Modeling:

For each class j:
* Find the probability of that class (P(y=j))
* Plot the gaussian distributions of each labels Pj(x)
* When a new point needs to be classified, the label which has the largest joint distribution is picked.  P(x,y) = P(y)P(x/y)                
   So the probability of any pair is the probability of that label, y, times the probability of seeing data x under that label y.

