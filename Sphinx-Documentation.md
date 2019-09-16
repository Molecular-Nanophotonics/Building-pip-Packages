# Sphinx Documentation

Sphinx is an Python package for automated documentation, e.g., [here](http://molecular-nanophotonics.github.io/pqreader).  


```
pip install sphinx
```

Enter the `/docs` folder and ecxecute:
```
sphinx-quickstart
```

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

Add:
```
.. automodule:: mypackage
    :members:
```
to the `index.rst` file:
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

To use the [Read the Docs][https://github.com/readthedocs/sphinx_rtd_theme] Sphinx Theme install the package with `pip`:
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
