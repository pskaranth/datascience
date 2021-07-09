
**Task**

Project to transliterate English to Hindi using Encoder-Decoder Attention Mechansim.
Encoder and Decoder with attention seems to be better at reducing loss and thus better at transliterating English to Hindi words.
Used GRU for Encoder and Decoder Models.



**Dataset**

https://www.microsoft.com/en-us/research/publication/report-of-news-2012-machine-transliteration-shared-task/

```
Publication:  “Report of NEWS 2012 machine transliteration shared task”
@inproceedings{Zhang:2012:RNM:2392777.2392779,
author = {Zhang, Min and Li, Haizhou and Kumaran, A. and Liu, Ming},
title = {Report of NEWS 2012 Machine Transliteration Shared Task},
booktitle = {Proceedings of the 4th Named Entity Workshop},
series = {NEWS '12},
year = {2012},
location = {Jeju, Republic of Korea},
pages = {10--20},
numpages = {11},
url = {http://dl.acm.org/citation.cfm?id=2392777.2392779},
acmid = {2392779},
publisher = {Association for Computational Linguistics},
address = {Stroudsburg, PA, USA},
}
```

**Reference**

DeepLearning - Padhai OneFourthLabs.


Issues faced:

1. RuntimeError: Input and hidden tensors are not at the same device, found input tensor at cpu and hidden tensor at cuda:0

https://stackoverflow.com/questions/58095627/how-to-fix-input-and-hidden-tensors-are-not-at-the-same-device-in-pytorch

This error occurs when PyTorch tries to compute an operation between a tensor stored on a CPU and one on a GPU. At a high level there are two types of tensor - those of your data, and those of the parameters of the model, and both can be copied to the same device like so:

device = torch.device("cuda" if torch.cuda.is_available() else "cpu")\
data = data.to(device)\
model = model.to(device)

2. "scatter_(): Expected dtype int64 for index." at one_hot.scatter_(2, max_idx, 1) 

hindi_enc = torch.zeros([len(word_)+1,1],dtype=torch.long).to(device)

Targets should have the right dtype, could resolve after adding dtype in the previous line.

