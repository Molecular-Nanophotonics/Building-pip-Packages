# Sphinx Documentation

Sphinx is an Python package for automated documentation. Click [here](http://molecular-nanophotonics.github.io/pqreader) to view an example. <br>

## Getting Started
To use Sphinx, install `sphinx` using `pip`:

```
pip install sphinx
```
In your project directory, create a folder named, e.g., `docs`. Then enter the `docs` folder and ecxecute:
```
sphinx-quickstart
```
You will be promted to answer some questions:
```
Separate source and build directories (y/n) [n]:
Name prefix for templates and static dir [_]:
Project name: mypackage
Author name(s): Author
Project version: 0.0.1
Project language [en]:
Source file suffix [.rst]: 
Name of your master document (without suffix) [index]:
Do you want to use the epub builder (y/n) [n]:
autodoc: automatically insert docstrings ... (y/n) [n]: y
doctest: automatically test code snippets ... (y/n) [n]: y
intersphinx: ... (y/n) [n]:
todo: ... (y/n) [n]:
coverage: ... (y/n) [n]:
imgmath: ... (y/n) [n]:
mathjax: ... (y/n) [n]:
ifconfig: ... (y/n) [n]:
viewcode: include links to the source code ... (y/n) [n]: y
githubpages: ... (y/n) [n]:
Create Makefile? (y/n) [y]: y
Create Windows command file? (y/n) [y]: y
```

After running `sphinx-quickstart` your project should look something like this:
```
MyPackage/
   doc/
      Makefile
      _build/
      _static/
      _templates/
      conf.py
      index.rst
      make.bat
   setup.py
   mypackage/
      __init__.py
      mypackage.py
```

In the  `index.rst` file, add:
```
.. automodule:: mypackage
    :members:
```
Your `index.rst` should look something like:
```
.. mypackage documentation master file, created by
   sphinx-quickstart on ...
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to mypackage's documentation!
====================================

.. toctree::
   :maxdepth: 2
   :caption: Contents:

.. automodule:: mypackage
    :members:
	
Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
```

In `mypackage.py` you have to format your documentations as follows:
```python
def my_function(arg1, arg2, arg3):
    """
    The discription ...
    
    Arguments:
        arg1: ... \n
	arg2: ... \n
	arg3: ...
    Returns:
        ret1: ... \n
        ret2: ...
    """
    
    return ret1, ret2
```

Finally, to build the documentation run:
```
make html
```
Your documentation can now be viewed opening `_build/html/index.html`

## Styling

To use the [Read the Docs Sphinx Theme](https://github.com/readthedocs/sphinx_rtd_theme) install the package with `pip`:
```
pip install sphinx-rtd-theme
```
To use the theme in your Sphinx project, you will need to add/change the following in your `conf.py` file:
```
import sphinx_rtd_theme

extensions = [
    ...
    'sphinx_rtd_theme',
]

html_theme = 'sphinx_rtd_theme'
```

