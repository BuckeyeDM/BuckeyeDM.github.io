---
layout: page
title: MILE
excludedFromNav: true
hideRight: true
permalink: /MILE/
---
### **MILE: A Multi-level Framework for Scalable Graph Embedding**
MILE is a multi-level framework for scalable graph embedding. It supports the majority of exising graph embedding techniques.
It can significantly improve the scalability of many graph embedding methods while potentially lifting the quality of embeddings.
Read our paper for more details. Here we describe how to use the code of MILE and add a new embedding method as the base embedding technique.

#### **Code and Data**
The code and dataset can be accessed [here](http://web.cse.ohio-state.edu/~liang.420/MILE_CODE.zip).

#### **Required Packages**
* tensorflow
* numpy
* scipy
* scikit-learn
* networkx
* gensim (only for using DeepWalk as base embedding method)
* theano (only for using NetMF as base embedding method)

#### **Input and Output**
* Input graph: For now, we only support undirected graph. The input graph can be weighted or unweighted. Two different formats are supported: edgelist and metis.
  - Edgelist: The input file must contain ".edgelist" extension. Each of line is an edge with an optional number for weight, separated by a space: *node1 node2 weight*. To save space, each edge should only show up once in the file with node1 as the one with larger id, i.e., node1 >= node2. If the graph is unweighted, *weight* can be left as empty. The node index does not need to be continuous as an internal node mapping will be conducted if necessary. See `./dataset/PPI.edgelist` for an example.
  - Metis: This input format has been commonly used for the METIS package. A detailed definition of the format can be found [here](http://people.sc.fsu.edu/~jburkardt/data/metis_graph/metis_graph.html). A graph of N nodes is stored in a file of N+1 lines. The first line contains two required numbers: the number of nodes and the number of edges, and an optional number to denote weigthed or unweighted graph: 0 or missing means unweighed while 1 means weighted. Each subsequent line lists the neighbors and edges weight (if any) of a node. Note that this format requires the index to be continous starting from **1**. See `./dataset/PPI.metis` for an example.

* Input ground truth for evaluation: If evaluation is enable (without `--no-eval`), a file proving ground truth for multi-class classification is required. It contains the list of nodes with known labels, where each line corresponds to one node. For each line, the first number is the index of the node (should be the same with the input graph) and the remaing numbers form a vector representation of the label (multi-class allowed). See `./dataset/PPI.edgelist.truth` or `./dataset/PPI.metis.truth` for examples.

* Output embeddings: if `--store-embed` is enabled, the embeddings will be saved under the `./dataset/` directory with extension of `.embeddings`. Each row correspond to one node, where the first number is the original node id and the rest is the vector representation.

#### **How To Run**
Use `python main.py` to run the code with all the default settings. Here are some useful arguments that can be passed into the program:
* data: name of the dataset, e.g., `--data PPI`.
* format: format of dataset, should be either *edgelist* or *metis*, e.g., `--format metis`.
* basic-embed: name of the base embedding method, e.g., `--basic-embed DEEPWALK`.
* coarsen-level: number of levels for coarsening, e.g., `--coarsen-level 1`.
* embed-dim: dimensionality for embedding, e.g., `--embed-dim 128`.
* store-embed: will store the embeddings if enabled.
* no-eval: will not evaluate the embeddings if set (.truth file will not be required then).
* workers: number of processes to run the code. 
* refine-type: refinement method, including `MD-gcn` (the one proposed in MILE), `MD-dump` (without model training), and `MD-gs` (using GraphSAGE).


#### **Adding a New Base Embedding Method**
Follow the steps below to add a new base embedding method:
  1. Implement the embedding method in `./embed.py` (e.g., `def deep_walk_embed(ctrl, graph):`).
  2. Add the choice of the new method name to `--baseic-embed` in the arguments of `./main.py` (*line-32*).
  3. Assign the name of the embedding method to `basic_embed` in `./main.py` (e.g., `basic_embed = deep_walk_embed`).


