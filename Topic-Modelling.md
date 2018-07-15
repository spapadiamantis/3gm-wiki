# Latent Dirichlet Allocation

## What is Latent Dirichlet Allocation and Non-Negative Matrix Factorization?

LDA is an algorithm that is used to discover the topics that are in a text. Topic modelling is an unsupervised model for detecting topics in a corpus and categorizing similar texts. Assume that you have some documents, for example Government Gazette Documents, and you want to cluster them to similar topics. Then LDA or NMF are ideal for this. The algorithms work in a different way regarding their mathematics.  We are going to use `sklearn` for topic modelling and clustering to similar topics. 

The code is located at `src/lda.py` 

## Topic Modelling Proceedure

The proposed way of modelling the topics is:

1. Parse raw texts
2. Remove punctuation numbers
3. Filter out words considered "junk" (i.e. really small words)
4. Lemmatize everything using Greek Lemmatizer provided from this GSoC project https://github.com/eellak/gsoc2018-spacy.  
5. Run LDA and NMF Algorithms and extract topics using grid search to find the best parameters
6. Gather topics to a graph

We can further our work by searching for connected components in the graph using a graph search algorithm such as Breadth-First Search

A visualization of topic models can be done using the `pyLDAvis` library. An example of this visualization is illustrated below:

![pyldavis](/home/marios/workspace/gsoc2018-3gm.wiki/pldavis.png)



The interactive Jupyter Notebook can be found at `src/lda_visualize.ipynb` . 



## References

1. [Medium Article](https://medium.com/mlreview/topic-modeling-with-scikit-learn-e80d33668730)
2. [sklearn Reference Manual](http://scikit-learn.org/stable/modules/generated/sklearn.decomposition.LatentDirichletAllocation.html)
3. Blei, David M., Andrew Y. Ng, and Michael I. Jordan. "Latent dirichlet allocation." *Journal of machine Learning research* 3.Jan (2003): 993-1022.

