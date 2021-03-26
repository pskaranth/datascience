{% include lib/mathjax.html %}

## Recurrent Neural Networks

RNN is recurrent as it evaluates the same function for the input at each layer. Subsequent outputs not only depends on the current input but also on the previous inputs.

It can be used in Sequence modelling where the task is to predict the next word. This is done by computing the probability of the occurence of the words in the sequence by taking into account the current and the previous word.

<p align="center"><img src="../img/RNN.png" width="300px" height="240px"></p>

The inputs are denoted by $$x_{i}$$\
The weights associated with input x is denoted by U\
The weights from the previous output is denoted by W\
The outout at each layer is $$y_{i}$$\
s is the state vector which is computed as a function of the outout of the previous output and current input with bias.

If the task is Sequence Classification, then the output $$\hat{y}$$  is computed for the entire sequence.

$$s_{i} = \sigma(Ux_{i} + Ws_{i-1}+b)$$
$$\hat{y} = O(Vs_{T} +c)$$ , T accounts for entire length of the inputs.

If the task is Sequence labeling, then the output is predicted at each layer.

$$s_{i} = \sigma(Ux_{i} + Ws_{i-1}+b)$$
$$\hat{y} = O(Vs_{i} +c)$$

Depending on the learning problem the output y can be computed for the entire sequence or at each and every layer.

The state vector (s) is of fixed size and at every step the information is computed. If a very long sequence is considered, the first input gets morphed into something else and it is difficult to know it's contribution to the state vector by the time it reaches the end of sequence.

So the goal is to selectively read, write and forget inputs we won't need so that the finite size for RNN can be maintained.

Using an analogy of sentiment analysis, we could say that we want to :
* Selectively forget the stop words.
* Selectively read the information added by previous sentiment bearing words.
* Selectively write the new information from the current word to the new state.

References:
* DeepLearning - Padhai OneFourthLabs
