# Cluster analysis

How the data group nicely and have common property

what clustering is ?

difficulties of clustering ?

number of clustering techniques

## what is clustering

* consist of grouping data into classes
  * what is similar and not similar
* translate into statistic
  * minimize the distant between object in a same class
  * maximize the distance between not similar object

## An ambiguous notion

* there are no natural grouping
* we have to decide how many group there is
* we decide arbitrary the number of group

## What's clustering good for ?

* exploratory data analysis and understanding
  * biology : taxonomy of living things
  * land use : identifying areas with similar properties
  * marketing : best use case
* preprocessing tool
  * quantization, coding and compression
    * example : image compression

## Quality

* good clustering mean
  * low withing-class similarity
  * high accross-class similarity
* but other factors count to
  * scalable (does it still work if we augmente data quantity)
  * dynamic behavior
  * ability to deal with noise
  * ...

## Two main philosophies

* clustering is to make a set of clusters
  * partitioning data : divide the entire data set
    * non-overlapping clusters
    * each object belongs to one and only one cluster
  * aggregating data : group similar data
    * nested clusters
    * hierarchical structure
* but other philosophies exist
  * density-based
  * grid-based
  * model-base
  * constraints-based

## about pairwise distances

* similar objects => notion of distance
* can measure any type of similarities
  * distance measures
  * similarity (no triangular inequality)
    * cosine, template matching, edit distance, generalized likelihood
  * conceptual measures
    * whatever one can thing of ...

## some typology elements

* exclusive or not ?
  * points might belong to several clusters (with or without weights)
  * decide if we want our classes to overlap or not
* fuzzy or not ?
  * fuzzy algorithm, a point is weighted with a weight between [0, 1]
* partial or not ?
  * only part of data is clustered
* homogeneous or not
  * cluster of very different shape
* well separated clusters
* center clusters
  * use of the center of the cluster
* contiguous cluster
* dense cluster

To select the most appropriate sol

* type of proximity or density measure
* sparseness
* attribute type

## the k-means algorithm

* idea
  * divide some data x, into K clusters
  * each clusters is represented by the mean value of their member : centroids
  * metric distance is used
  * minimize the overall quantization error

## the art of k-means clustering

* the distance is the key
  * mean has to have a meaning
  * but we can use the median instead (the k-medians or k-medioids algorithm)
* convergence = nothing moves anymore
  * convergence is guaranteed
  * often in 10 to 20 iterations
* initialization is tricky

## initialization issues

* very sensitive
* solution
  * multiple runs
    * costly
    * what to do with dead-cluster
  * hierarchical k-means
    * linde-buzo-gray algorithm (aka bisecting k-means)
      * basically add slowly cluster through time
* no guarranty that solution found is global solution

## pros and cons

* pro
  * simple, clear and popular
  * decently efficient
  * guaranteed convergence
  * can accomodate any shape (with enough clusters)
* cons
  * initialization and local optima
  * need to define the number of clusters
  * convex clusters of roughly the same size and densities
  * tends to create unbalanced cells
  * highly sensitive to noise and outliers

## hierarchical clustering

* idea
  * progressively generate clusters by merging or divising data
  * generate nested clusters
  * can be visualized as dendogram
* technics
  * find pairwise of points that are the closest of each another
* it's good because we group data together
* it's bad because
  * there are many clusters
  * can't interprete clusters
* solution
  * cut the dendogram at some point

## Agglomerative vs divisive

* agglomerative bottom-up clustering
  * bottom-up construction of the dendogram by progressively merging clusters
* divisive bottom-up clustering
  * top-down construction of the dendogram
  * DIANA

## implementation : proximity matrix and bottom-up clustering

* how do we compute de distance between each classes
  * metric distance : use center of gravity
  * computing distance is called linkage : similarity between classes

## linkage types

linkage = how to measure the distances between clusters

* single linkage
  * take the min distance
  * for well-separated classes only
* total linkage
  * take the max distance
  * favors large clusters
* average linkage
  * take the average distance
  * robut to noise and outliers but biased towards globular clusters
* ward's linkage
  * increase variance for the cluster being merged

## pro and cons

* pro
  * better than k-means with non-metric distances
  * can combine metrics and cluster balancing criteria
  * possibility to define a posteriori the number of clusters (though not so easy in pratice)
    * define the stopping criteria
* cons
  * quite slow
  * local optima may not be globally good
  * cutting the dendogram is not as easy as it seems to be

## mining tv sequences with bottom-up clustering

* visual clustering and audio clustering
* isolate the presentater
* found when a new topic is introduced

## similarity graphs for spectral clustering

* data point = node in a graph
* edges encode the similarity between two nodes with weights wij
* epsilon-neighbor graphs
* k-nearest neighbor graphs
* fully connected graphs

## graph laplacian

* property of laplacian matrix
  * L as n non-negative, real valued eigenvalues
  * the smallest eigenvalue is 0 and corresponds to the unit eigen vector
  * the multiplicity of the eigenvalue 0 is the number of connected components
* exploit the eigenvalues of the laplacian

* strong links with
  * graph cut algorithms (NVut, RationCut, MinMaxCut)
  * random walks theory (Markov clustering)

## Density-based clustering in a nutshell

* track density-connected points = neighborhood analysis

* db scans
  * label points
    * core points : enough point around
    * border points : not enough points around
    * noise points : none of the above
  * eliminate noise points
  * create clusters from core points
  * assign borders to clusters

## Clustering with obstacles
