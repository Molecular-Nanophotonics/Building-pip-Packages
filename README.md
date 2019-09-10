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

## Setup your Project

### 

You will now create a handful of files to package up this project and prepare it for distribution. Create the new files listed below - you will add content to them in the following steps.

```
MyExample/
  mypackage/
    __init__.py
    myexample.py
  setup.py
  LICENSE
  README.md
```


Create a setup file setup.py in your package. This file will contain all your package metadata information. 

```
import setuptools

with open("README.md", "r") as f:
    long_description = f.read()

setuptools.setup(
    name="myexample",
    version="0.0.1",
    author="Author Name",
    author_email="author@example.de",
    description="Discription of my Package",
    long_description=long_description,
    long_description_content_type="text/markdown",
    url="https://github.com/molecular-nanophotonics/myexample",
    packages=setuptools.find_packages(),
    classifiers=[
        "Programming Language :: Python :: 3",
        "License :: OSI Approved :: MIT License",
        "Operating System :: OS Independent",
    ],
)

```


The next step is to generate distribution packages for the package. These are archives that are uploaded to the Package Index and can be installed by pip.

Run the following command from the same directory where setup.py is located:

```python3 setup.py sdist bdist_wheel```

This command should generate two files in the dist directory:

```
dist/
  mypackage-0.0.1-py3-none-any.whl
  mypackage-0.0.1.tar.gz
```

## Uploading the Distribution Packages

Run Twine to upload all of the archives under `dist`:
```
python -m twine upload dist/*
```

You will be prompted for the username and password you registered with PyPI. After the command completes, you should see output similar to this:
```
Enter your username: molecular-nanophotonics
Enter your password:
Uploading distributions to https://upload.pypi.org/legacy/
Uploading myexample-0.0.1-py3-none-any.whl
100%|█████████████████████████████████████| 
Uploading myexample-0.0.1.tar.gz
100%|█████████████████████████████████████| 

View at:
https://pypi.org/project/pmyexample/0.0.1/
```
