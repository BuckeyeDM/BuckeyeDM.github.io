---
layout: page
title: PRO-HEAPS
excludedFromNav: true
hideRight: true
permalink: /PRO-HEAPS/
---

# PROphetic HEuristic Algorithm for Path Searching (PRO-HEAPS)

## Datasets
### Stack Overflow
This is the dataset preprocessed from the [Stack Overflow dump](https://archive.org/details/stackexchange). 
We parsed each post and constructed a heterogeneous information network (HIN) by dividing entities into the vertex labels: question, answer, tag and user. 
In this version of dataset, we remove the directionality of edges since each edge always connects nodes of different labels. 
We do not provide the weights of edges in this dataset. The weights can be defined based on the interestingness, such as time recency and popularity of questions, 
which can be inferred by the attributes of nodes. Here are the lists of data files:

* [HIN graph](http://web.cse.ohio-state.edu/~liang.420/datasets/SOF_HIN.edgelist.gz): This is the HIN graph in edgelist format. Each line (except the The first line) represents an edge with format "node_id node_id \[node_label\] \[node_label\] edge_label". For the node labels, "[0]" represents the Question, "[1]" represents the Answer, "[2]" represents Tag, "[3]" represents User. Labels of edges can be inferred directly from the vertex labels. In total, the graph contains 21,579,657 nodes and 53,325,635 edges.

* [Questions](https://drive.google.com/open?id=0B51ZquKpPTzMQ1JndlMtSUY3azg): This file provides detailed information of each question. It has five columns separated by " ### ". The first column is the id of the question. The second column is the timestamp of the question. The third column is the number of views of the question. The fourth column is the score of the question provided by Stack Overflow. The last column is the content of the question.

* [Answers](https://drive.google.com/open?id=0B51ZquKpPTzMQnU1MGN4cm1kSGs): This file provides detailed information of each answer. It has four columns separated by " ### ". The first column is the id of the answer. The second column is the timestamp of the answer. The third column is the score of the answer provided by Stack Overflow. The last column is the content of the answer.

* [Tags](http://web.cse.ohio-state.edu/~liang.420/datasets/Tag.new.gz): This file provides the detailed information of each tag. It has two columns separated by " ### ". The first column is the id of the tag and the second column is the text of the tag.

* [Users](http://web.cse.ohio-state.edu/~liang.420/datasets/User.new.gz): This is a file describing the mapping of the user id in the graph to the original id in the raw dataset. It has two columns separated by " ### ". The first column is the id of the user in our HIN and the second column is the id of the user in the original dataset. The original dataset of users can be downloaded [here](https://drive.google.com/open?id=0B51ZquKpPTzMMjA2cE16ZFV3Wjg).
