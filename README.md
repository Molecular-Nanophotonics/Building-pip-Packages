# Building pip Packages

This tutorial shows how to create a Python pip package. It will show you how to add the necessary files and structure to create the package, how to build the package, and how to upload it to the Python Package Index (https://pypi.org).

If you want to make your package publicly accessible you can upload it on PyPi. So, first of all, register yourself on PyPi: https://pypi.org/account/register/.

You might use the Molecular Nanophotonics accout: <br>

Username: molecular-nanophotonics
Password: default password + mona

I assume that you upload your package code on the groups GitHub account. The README.md from the GitHub repository will be directly used  as documentation of your package. 

## Install Required Tools

```
python -m pip install --upgrade pip setuptools wheel
python -m pip install tqdm
python -m pip install --user --upgrade twine
```

Create a setup file setup.py in your package. This file will contain all your package metadata information. 

```
import setuptools

with open("README.md", "r") as f:
    long_description = f.read()

setuptools.setup(
    name="mypackage",
    version="0.0.1",
    author="Author Name",
    author_email="author@physik.uni-leipzig.de",
    description="Discription of the Package",
    long_description=long_description,
    long_description_content_type="text/markdown",
    url="https://github.com/molecular-nanophotonics/mypackage",
    packages=setuptools.find_packages(),
    classifiers=[
        "Programming Language :: Python :: 3",
        "License :: OSI Approved :: MIT License",
        "Operating System :: OS Independent",
    ],
)

```
