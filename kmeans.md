{% include lib/mathjax.html %}

## K Means

It is an algorithm under the section of unsupervised learning as it does not have labeled outputs. The goal is to group data with similar features in the form of clusters.
Applications include _Recommendation Engines, Image Segmentation_.

## Steps to follow for implementing kmeans:

- Decide how many clusters are needed which is given by _k_.
- $$\mu_{1} , \mu_{2}$$ centers are randomly initialised.
- Repeat until convergence:
    - Each point is assigned to it's closest cluster center.

      The closest cluster center is obtained by considering the minimum average squared distance between points and their nearest representatives:
  
      $$cost(\mu_{1} ,.., \mu_{k}) = \sum_{i=1}^nmin||x_{i}-\mu_{k}||^{2} $$
  
    - Each $$\mu_{j}$$ is updated with the mean of the points assigned to it.

The last 2 steps are repeated until it converges to a  local optimum.

<div style="width:100%;height:0;padding-bottom:42%;position:relative;"><iframe src="https://giphy.com/embed/gDcfQUff9v6YdAttKp" width="100%" height="100%" style="position:absolute" frameBorder="0" class="giphy-embed" allowFullScreen></iframe></div><p><a href="https://giphy.com/gifs/gDcfQUff9v6YdAttKp">via GIPHY</a></p>

## K means Initialisation
With k means, different initialisation might end up in different clusters. To avoid this, one of the tricks is to have extra _k_ clusters and once the algorithm converges prune the extra k centers which are either very far or very few points assigned to the centers.

A better initialisation method called _K means++_ can be used to achieve better results of the clusters:
- In this; a random data point x is chosen as center given by $$\mu_{1}$$
- To pick the next center $$\mu_{2}$$ , a point that is farthest to the first $$\mu_{1}$$ is chosen.The probability of picking a point x is proportional to the distance from x     to the center  $$\mu_{1}$$ squared.

  $$ P(x) \propto (x-\mu_{k})^{2} $$
  
 - Next center $$\mu_{3}$$ is picked based on the farthest distance to both $$\mu_{1}$$ and $$\mu_{2}$$.
 
For larger data sets, another initialisation method called _Sequential K-means_ can be considered:
- In this; centers $$\mu_{1}$$, $$\mu_{2}$$ ,..,$$\mu_{k}$$ are chosen randomly.
- Counts of each centers are set to $$n_{1}$$, $$n_{2}$$ ,..,$$n_{k}$$ = 1.
- Get the next point x and let $$\mu_{j}$$ be the closest center to x.
- Update $$\mu_{j}$$ and $$n_{j}$$ given by

$$\mu_{j} = \frac{n_{j}\mu_{j}+ x}{n_{j}+1}$$

$$n_{j} = n_{j} + 1 $$


