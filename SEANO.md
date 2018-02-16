---
layout: page
title: SEANO
excludedFromNav: true
hideRight: true
permalink: /SEANO/
---

### Semi-supervised Embedding in Attributed Networks with Outliers (SEANO)
SEANO provides an effective method for graph embeddings on attributed networks that contains outliers.
For more technical details, refer to [our paper](https://arxiv.org/pdf/1703.08100.pdf). Here we publish our
code and dataset along with a brief instruction on how to run the code.

#### Code and Data
They can be downloaded from [here]().

#### Required packages
* tensorflow
* numpy
* scipy


#### Inputs
The list of required files of input is shown below. All index starts from 0 and the files are stored in **cPickle** format.
`xxx` means the name of the dataset, e.g., `cora`.
- `xxx.X`: attributes of all nodes (sorted by id), e.g., `cora.X`.
- `xxx.Y`: label vectors of all nodes, e.g., `cora.Y`.
- `xxx.graph`: graph stored in dictionary format. node id --> list of neighbors.
- `xxx.labeled.index`: labeled node for semi-supervised training.
- `xxx.val.index`: index of validation nodes.
- `xxx.test.index`: index of testing set. In the inductive case, this part will be excluded from training.
- `xxx.rnd_walks.npy` (optional): random walk files. If missing, new random walks will be generated and written to this file.

#### Outputs
* If `--store-embed` is enabled, the embeddings will be saved to the `./data/` directory with `.embeddings` extension in text format.
* If `--store-score` is enabeld, the outlier scores will be saved to the `./data/` directory with `.score` extension in text format.


#### How to run
Use `python main.py` to run the code with the default parameters. For more details of the arguments, see main.py. 
You might need to use the validation dataset to tune some hyper-parameters (e.g., `g_batch_size`, `g_sample_size`, etc.) 
for your own dataset.
