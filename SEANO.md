---
layout: page
title: SEANO
excludedFromNav: true
hideRight: true
permalink: /SEANO/
---

### **SEANO: Semi-supervised Embedding in Attributed Networks with Outliers**
SEANO provides an effective method for graph embedding on attributed networks that contain outliers.
For more technical details, refer to [our paper](https://arxiv.org/pdf/1703.08100.pdf). Here we publish our
code and dataset along with a brief instruction on how to run the code.

#### **Code and data**
They can be downloaded from [here](http://ruan.cse.ohio-state.edu:8080/SEANO_CODE.zip).

#### **Required packages**
* tensorflow
* numpy
* scipy

#### **How to run**
Use `python main.py` to run the code with the default parameters. For more details of the arguments, see `main.py`. 
You might need to use the validation dataset to tune some hyper-parameters (e.g., `graph_context_batch_size`, `label_context_batch_size`, etc.) 
for your own dataset. 

#### **Inputs**
The list of required input files is shown below. The node index should be **continuous starting from 0** and all the input files are stored in **cPickle** format.
`xxx` means the name of the dataset, e.g., `cora`.
- `xxx.X`: attributes of all nodes (sorted by id), e.g., `cora.X`.
- `xxx.Y`: label vectors of all nodes, e.g., `cora.Y`.
- `xxx.graph`: graph stored in dictionary format. node id --> list of neighbors.
- `xxx.labeled.index`: labeled nodes for semi-supervised training.
- `xxx.val.index`: index of validation nodes.
- `xxx.test.index`: index of testing set. In the inductive case, this part will be excluded from training.
- `xxx.rnd_walks.npy` (optional): random walk files. If missing, new random walks will be generated and written to this file.

#### **Outputs**
All the output files are located in `./output/`, all of which are stored in **cPickle** format. There are three outputs:
* `xxx.embed`: Embedding of each node in the graph.
* `xxx.pred_label`: Predicted label of each node.
* `xxx.outlier_score`: Outlier score of each node.

Note: if inductive learning is enabled through `--inductive`, the prefix of the outputs would be `xxx_ind.`.

#### **Reference**
J. Liang, P. Jacobs, J. Sun, S. Parthasarathy. "Semi-supervised Embedding in Attributed Networks with Outliers". To appear in *Proceedings of SIAM International Conference on Data Mining (SDM'18)*, 2018. \[[PDF](https://arxiv.org/pdf/1703.08100.pdf)\]\[[bib](publications/SDM18.txt)\]
