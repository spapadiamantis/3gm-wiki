# Latent Dirichlet Allocation

## What is Latent Dirichlet Allocation and Non-Negative Matrix Factorization?

LDA is an algorithm that is used to discover the topics that are in a text. Topic modelling is an unsupervised model for detecting topics in a corpus and categorizing similar texts. Assume that you have some documents, for example Government Gazette Documents, and you want to cluster them to similar topics. Then LDA or NMF or  is a way to go. The mathematical basis underpinning NMF is quite different from LDA. We are going to use sklearn for topic modelling and clustering to similar topics. 

The code is located at `src/lda.py` 

## Topic Modelling Proceedure

The proposed way of modelling the topics is:

1. Parse raw texts
2. Remove punctuation numbers
3. (Optionally) Lemmatize everything
4. Run LDA Algorithm and extract topics
5. Gather topics to a graph

We can further our work by searching for connected components in the graph using a graph search algorithm such as Breadth-First Search

**References**

[1] [Medium Article](https://medium.com/mlreview/topic-modeling-with-scikit-learn-e80d33668730)

