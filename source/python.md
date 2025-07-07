# Python

Python is most often best installed using a package from [https://www.python.org/downloads/](https://www.python.org/downloads/).

Picking a version is a tradeoff between length of future maintenance and support, functionality, and time for 3rd party library developers to update their code to the latest versions available.

As a rule of thumb, find the current major development (pre-release) version (at time of writing in May 2022, this is Python 3.11) and drop down a couple of versions (to, in this case 3.9). This should give a reasonable balance between longevity and compatibility with 3rd party libraries.

## Virtual Environments and Package Management Tools

### Virtualenv 

After installation, it's good practice to create a python virtual environment using [`virtualenv`](https://packaging.python.org/en/latest/guides/installing-using-pip-and-virtual-environments/) in which to cultivate your development envrionment.

Two advantages of doing this are:

* you can more confidently experiment with new modules and modifications in an isolated virtual environment, and if something goes wrong you can trash and start again
* using the pip freeze method to store an environments contents, this rebuild process can be automated and ported over to other environments where someone else might want to run your code

Creating a virtual environment usually requires defining some name and location for your environment content, which after `cd`-ing to on your terminal session, you can create using the following commands:

```
pip install virtualenv
virtualenv devpy
```

Having created your virtual environment, activate it using the `activate` script located in the environment's `scripts` or `bin` folder, which will update your session's path variables such that the python executables and installation procedures will deploy new libraries in isolation to that environment.

To store a copy of a populated environment's contents, use the command

```
pip freeze
```

To see all the modules and their version-numbers.

This output can be saved to a `requirements.txt` file which can be ported to another machine, or stored somewhere convenient and can then be used as configuration to a `pip install` command to replicate that environment elsewhere, or on the same machine at a future date.

```
pip install -r requirements.txt
```

### Pipenv

[Pipenv](https://docs.pipenv.org/) is an advanced alternative to virtualenv that more tightly integrates pip and virtualenv. It can make managing multiple python versions and virtual environments relatively easily.

### Conda

[Conda](https://github.com/conda/conda) is an open-source packagement system and environment management system for installing multiple versions of software packages and their dependencies (and switching between them).

One reason for considering conda would be where python integration with GPUs for scientific computing and machine learning is required, as conda can help manage the broader ecosystem of drivers, libraries and tools for GPU accelerated projects (e.g. CUDA NVIDIA drivers)

