{% include lib/mathjax.html %}

## K- Nearest Neighbour

### Projects 
- Identifying digits using MNIST data set - [KNN_MNIST](https://github.com/pskaranth/thelearningcurve/tree/master/Classification/KNN)

To classify a new point:
 - Find the k nearest neighbors in the training set using a distance metric. The commonly used distance metric is Euclidean distance.
   For two vectors $x, y \in \mathbb{R}^d$, their Euclidean distance is defined as 
$$\|x - y\| = \sqrt{\sum_{i=1}^d (x_i - y_i)^2}.$$
   Often we omit the square root, and simply compute _squared Euclidean distance_:
$$\|x - y\|^2 = \sum_{i=1}^d (x_i - y_i)^2.$$
 - Return the most frequently occuring label amongst the k nearest points.

How do we set K?
In order to set the K properly, we use Cross Validation technique.

Cross Validation:
- Choose K(3,5) randomly. For  each K:
- Split the data into n fold groups. (10 fold groups)
- Each group is considered as  a test/validation set and remaining groups together form the training set. 
- A model is fit on the training set and evaluated on a test set using K-NN classifier.
- For example : when  K=3 , in order to classify a new image; we find it’s three closest images in the training set and then return the most frequently occuring label.
- Find the error estimate. Choose the value of  k that results in the lowest average error rate on these validation sets. That is how we find K in K nearest neighbour classification.

 

