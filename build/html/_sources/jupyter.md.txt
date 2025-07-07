# Jupyter

Jupyter (notebook) is an open source web application that allows editing and running notebook documents within a browser. A common use-case is as an integrated python/data science development environment.

Each notebook is given a title that informs that notebook's filename on disk, and consists of a number of input and output *cells*.

Input cells can be one of a number of sub-types, including 
* Markdown - enabling markdown text to be entered, which once "executed" is displayed using the markdown formatting. This enables richly formatted documentation be embedded within a notebook, using all of the common markdown conventions. 

* Code - a code input cell enables python (or other code, see *Kernel* later) be entered and edited. Code can be executed from within a cell, and generally any results output by that code to standard IO are populated in a new following output cell wherein the results (or error messages where generated) are displayed.

* Raw - values in raw cells is not rendered using markdown, nor is there any ability to execute it. It appears to largely be used to feed documentation generation tools (e.g. Sphinx) with additional or specifically coded information to drive document generation. 

For a developer/data scientist/business analyst, the main advantage in adopting and working with jupyter notebook is the interactive way it enables exploring data, by writing scripts to generate visualisations, machine learning and analysis and other data science and analytical workflows.


## Installation

Once any [python environment](python.md#python) is in place, Jupyter notebook can be [installed](https://jupyter.org/install) via `pip`

```
pip install notebook
```