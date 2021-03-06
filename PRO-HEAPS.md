---
layout: page
title: PRO-HEAPS
excludedFromNav: true
hideRight: true
permalink: /PRO-HEAPS/
---
# PROphetic HEuristic Algorithm for Path Searching

## Datasets
### 1. Stack Overflow
This is a dataset preprocessed from the [Stack Overflow dump](https://archive.org/details/stackexchange). 
We parsed each post and constructed a heterogeneous information network (HIN) by dividing entities into the vertex labels: question, answer, tag and user. 
In this version of dataset, we remove the directionality of edges since each edge always connects nodes of different labels. 
We do not provide the weights of edges in this dataset. The weights can be defined based on the interestingness, such as time recency and popularity of questions, 
which can be inferred by the attributes of nodes. Here are the lists of data files:

* [HIN graph](http://34.214.78.14/SOF/SOF_HIN.edgelist.gz): This is the HIN graph in edgelist format. Each line (except the The first line) represents an edge with format "node_id node_id \[node_label\] \[node_label\] edge_label". For the node labels, "[0]" represents the Question, "[1]" represents the Answer, "[2]" represents Tag, "[3]" represents User. Labels of edges can be inferred directly from the vertex labels. In total, the graph contains 21,579,657 nodes and 53,325,635 edges.

* [Questions](https://drive.google.com/open?id=0B51ZquKpPTzMQ1JndlMtSUY3azg): This file provides detailed information of each question. It has five columns separated by " ### ". The first column is the id of the question. The second column is the timestamp of the question. The third column is the number of views of the question. The fourth column is the score of the question provided by Stack Overflow. The last column is the content of the question.

* [Answers](https://drive.google.com/open?id=0B51ZquKpPTzMQnU1MGN4cm1kSGs): This file provides detailed information of each answer. It has four columns separated by " ### ". The first column is the id of the answer. The second column is the timestamp of the answer. The third column is the score of the answer provided by Stack Overflow. The last column is the content of the answer.

* [Tags](http://34.214.78.14/SOF/Tag.new.gz): This file provides the detailed information of each tag. It has two columns separated by " ### ". The first column is the id of the tag and the second column is the text of the tag.

* [Users](http://34.214.78.14/SOF/User.new.gz): This is a file describing the mapping of the user id in the graph to the original id in the raw dataset. It has two columns separated by " ### ". The first column is the id of the user in our HIN and the second column is the id of the user in the original dataset. The original dataset of users can be downloaded [here](https://drive.google.com/open?id=0B51ZquKpPTzMMjA2cE16ZFV3Wjg).

### 2. DBLP
This is a dataset preprocessed from the [DBLP dump](http://dblp.uni-trier.de/xml/). This dataset contains four types of nodes: author, paper, venue, and terminology. The terminologies are parsed from the title of each paper.  
* [HIN graph](https://drive.google.com/file/d/0BxYPnHj3Q4pSOWJUUjdPMFRRMWs/view?usp=sharing): This is the HIN graph in edgelist format. Each line (except the The first line) represents an edge with format "node_id node_id \[node_label\] \[node_label\] edge_label wgt_year". 
For the node labels, "[0]" represents the Paper, "[1]" represents the Author, "[2]" represents Venue, "[3]" represents Term.
In total, the graph contains 2,241,258 nodes and 14,747,328 edges. 

### 3. Enron
This is a dataset containing Email messages sent between employees of the Enron
corporation (see [here](https://www.cs.cmu.edu/~./enron/) for the original dataset). 
We created a HIN based on the raw dataset with four types of vertex labels:
person, Email address, Email message, and topic. For the topics, we created fifty topics
using the LDA model [Blei et al. 2003], and linked each Email message to the closest three
topics.
* [HIN graph](https://drive.google.com/file/d/0BxYPnHj3Q4pSemluR0dTb1VfQ1U/view?usp=sharing): This is the HIN graph in edgelist format. Each line (except the The first line) represents an edge with format "node_id node_id \[node_label\] \[node_label\] edge_label wgt". For the node labels, "[0]" represents the person, "[1]" represents Email address, "[2]" represents Email message, "[3]" represents topic.
In total, the graph contains 46,463 nodes and 613,838 edges.

## Reference
The datasets should only be used for academic purpose. Please consider citing the following paper if you use the above datasets.

* **J. Liang**, D. Ajwani, P. Nicolson, A. Sala, S. Parthasarathy. "What Links Alice and Bob? Matching and Ranking Semantic Patterns in Heterogeneous Networks". In *Proceedings of the 25th International World Wide Web Conferences (WWW'16)*, pp. 879-889, 2016. \[[PDF](./publications/WWW16_PRO-HEAPS.pdf)\]\[[bib](publications/WWW16.txt)\]
