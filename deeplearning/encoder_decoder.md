{% include lib/mathjax.html %}

## Encoder-Decoder Models

Combination of RNN, FNN models makes up for the encoder-decoder model.\
Encoder takes the input, encodes it into a vector and the output of encoder is passed to a decoder as the input.

In case of image captioning, CNN networks are used for encoding images into a vector.\
The output of the encoder is passed to a decoder(RNN). Decoder generates the probability distribution of the generated output.\
We calculate the Loss function and back propogate the network all the way till Encoder to learn the parameters.

In the end, we find the argmax to get the predicted output from the network.


## Encode-Attend-Decode Models/Seq2Seq with Attention

Instead of passing entire encoded output to the network, we can pass only the relevant information to the decoder network. This is done by providing more weights to the selected encoder outputs.

This is _Attention mechanism_. It identifies parts of the input sequence which are relevant to each word in the output and we use the information to select the appropriate output.

The goal is to compute a _Context Vector_. This is a weighted sum of all the (encoded RNN state at jth time step )inputs(_h_) and the importance of the word(_α_) at the $$t^{th}$$ timestep.

$$c_{j} =\sum_{j=1}^T α_{jt} h_{j} $$  

The parameter $$α_{jt}$$ used above has to be learned from the data. It denotes the probability of focusing on the jᵗʰ word to produce the tᵗʰ output word.\
It is the softmax function of $$e_{jt}$$

$$α_{jt} = \frac{exp(e_{jt})}{\sum_{i=1}^n exp(e_{jt})}$$ 

Parameter $$e_{jt}$$ depends on the current state(_s_) of the decoder and the encoder output state(_h_).\
To enable this we define a function,

$$e_{jt} = f_{ATT}(s_{t-1},h_{j})$$

The most commonly used parametric form or function to compute the ejt is given below:

$$ e_{jt}= V^{T}_{att}(U_{att}s_{t-1}+W_{att}h_{j})$$ 


To learn the parameter ejt, we have introduced additional parameters Vₐtt, Uₐtt and Wₐtt. Where Uₐtt denotes weights associated with the input of an encoder, Wₐtt denotes weights associated with the decoder hidden state and Vₐtt denotes weights associated with the output of a decoder. These parameters will also be learned along with other parameters of the encoder-decoder model.

Some examples where encoder-decoder models could be used:

#### Language Prediction:

Given the t-i words we would like to predict the value of $$t^{th}$$ word.

We want to compute 

y = argmax $$ P(y_{1},y_{2},..y_{t-1}) $$

RNN encodes inputs to the state vector $$s_{t}$$ and gets passed on . The final step uses the feed forward network and decodes the output to predict the next word.

#### Machine translation:

This falls under sequence to sequence generation problems.
We use RNN for encoding inputs.
The output of the above encoder is used as an input vector to another RNN model which is a decoder.

#### Machine transliteration:

Sequence to sequence generation problem.
Encoder could be RNN/LSTM, the output at the last step is fed to a decoder which is again a RNN.


References:
* DeepLearning - Padhai OneFourthLabs
