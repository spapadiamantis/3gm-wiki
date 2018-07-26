# Ranking Laws using PageRank

The process of cross-linking of legislation is an ideal case in which we can use ranking algorithms such as **PageRank** in order to rank laws and extract the significance of them.

### What is PageRank and how does it work?

Consider a web browser which selects randomly a link of a page that he is currently on and redirects there. We can imagine the surfing process as a Markov Chain on the set of pages (vertices) V in which the probability of jumping from a page x to a page y is uniform, i.e.

<p align="center">

<img src="eq1.png">

</p>

The state space large but finite. Suppose that this chain is irreducible, so it must have an invariant distribution π. This hypothesis is equivalent to the graph being one connected component. This is not realistic as this graph would have more than one connected components, but it is an ideal reduction to showcase that the invariant distribution is a perfect significance ranking metric.  Indeed the ergodic theorem tells us that asymptotically the time we are going to spend on each page is given by its stationary distribution probability π(x). In mathematical language: 

<p align="center">

<img src="eq2.png">

</p> 

In that sense, the invariant (or stationary) distribution is a very good **significance** measure.

We can therefore let the significance σ(x) of each page be given as:

<p align="center">

<img src="eq3.png">

</p>

This is indeed the definition of a stationary distribution. 

How are we going to make the graph which has more than one connected components one connected component?

The idea is pretty simple. Consider tossing a coin with probability α of being heads. Therefore we can define the following transition probabilities for the set of pages V.

<p align="center">

<img src="eq4.png">

</p>

The Markov Chain with probabilities p(x,y) will give σ(x) > 0 for all pages in the graph.

