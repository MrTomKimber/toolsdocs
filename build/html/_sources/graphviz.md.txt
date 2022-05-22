# Graphviz

[Graphviz](https://graphviz.org/) is open source graph vizualisation software enabling diagrams to be automatically laid-out in displays using a number of optimised layout algorithms.

[Installation](https://graphviz.org/download/) instructions vary according to environment, but it tends to be available via Linux packaging manager repositories, as well as Mac OS [ports](https://www.macports.org/) and [Homebrew](https://brew.sh/). For windows, a [number of installers](https://graphviz.org/download/#windows) exist for download.

Graphviz can also be compiled direct for installation from [source-code](https://graphviz.org/download/source/)

Graphviz has a [long and well documented history](https://graphviz.org/theory/), the algorithm and code at its core having been written sometime in the early 1990's.

## PyGraphviz - python package

[PyGraphviz](https://pygraphviz.github.io/) is a python interface into the Graphviz layout package - enabling the power of Graphviz to be accessed programatically.

A good example installation in Linux can be started using the following, which includes both the graphviz and pygraphviz installation commands:

```
sudo apt-get install graphviz graphviz-dev
pip install pygraphviz
```

But other installation instructions exist for [alternative environments](https://pygraphviz.github.io/documentation/stable/install.html).
