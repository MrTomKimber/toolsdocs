# Reusable Analysis Patterns

## Clustering

Where many data points are present in a piece of analysis, it can be useful to break the data down into different groups. If no external classification scheme can be applied, it falls to the analyst to find a meaningful way of classifying the content of the data.

After identifying groups, their individual properties can be compared and contrasted with one another, usually providing a means to construct an illustrative narrative, or to tease out group-specific relationships with other data that might have been otherwise lost across a noisy channel.

Often, applying a clustering algorithm to a large dataset can help make sense of it, and break it open for more in-depth analysis.

Many data-science algorithms exist for performing clustering, but a few choice reciepes are presented here with some installation and operational considerations.

### Hierarchical (Agglomorative) Clustering

The python [scipy library](https://docs.scipy.org/doc/scipy/index.html) contains a wealth of methods for analysing data, but specifically for clustering, the [hierarchy](https://docs.scipy.org/doc/scipy/reference/cluster.hierarchy.html#module-scipy.cluster.hierarchy) sub package contains powerful methods and utilities for performing clustering analysis on datasets.

To install scipy, switch to your virtual environment and run the following command:

```
pip install scipy
```

Clustering is the process of breaking a dataset into a number of subgroups or clusters based on percieved similarities or differences between records. 

[scipy.cluster.hierarchy.linkage](https://docs.scipy.org/doc/scipy/reference/generated/scipy.cluster.hierarchy.linkage.html#scipy.cluster.hierarchy.linkage) is a great utility for performing clustering and is fast and easy to use. Other clustering options come built into sklearn. Some options exist for [rolling one's own using only numpy](https://blog.paperspace.com/speed-up-kmeans-numpy-vectorization-broadcasting-profiling/). 


### K-Means Clustering

### NNMF Clustering

### Choosing a number of clusters - finding "the elbow"

## Curve Fitting

## Network Analysis
