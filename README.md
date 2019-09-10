# Python pip Packages

This tutorial shows how to build a Python pip package and how to upload it to the Python Package Index, e.g., https://pypi.org.

## Install Required Tools

```
python -m pip install --upgrade pip setuptools wheel
python -m pip install tqdm
python -m pip install --user --upgrade twine
```

## Setup your Project

For distribution your project need to be structured as follows: 

```
MyPackage/
  mypackage/
    __init__.py
    mypackage.py
  setup.py
  LICENSE
  README.md
```

The content of each file will be discussed in the following steps.

## Creating setup.py

Create a setup file `setup.py` in your package. This file will contain all your package metadata information. 

```
import setuptools

with open("README.md", "r") as f:
    long_description = f.read()

setuptools.setup(
    name="mypackage",
    version="0.0.1",
    author="Author Name",
    author_email="author@example.de",
    description="Discription of my package",
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

## Creating README.md

Create `README.md` and enter, e.g.:

```
# Example Package

This is a simple example package. 
```

It si recommended that you upload your package code on the groups [Github](https://github.com/molecular-nanophotonics) repository. The README.md from the GitHub repository will then be directly used as documentation of your package. 

## Creating a LICENSE

It’s important for every package uploaded to the Python Package Index to include a license. For example, if you had chosen the MIT license, open the `LICENSE` file and enter the license text:
´´´
Copyright (c) 2018 The Python Packaging Authority

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
´´´

## Generating Distribution Packages

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

If you want to make your package publicly accessible you need to upload it on PyPI. The credentials for the Molecular Nanophotonics PyPI account are: <br>

Username: `molecular-nanophotonics` <br>
Password: `default password + mona`

Run Twine to upload all of the archives under `dist`:
```
python -m twine upload dist/*
```
You will be prompted for the username and password you registered with PyPI. After the command completes, you should see output similar to this:
```
Enter your username: molecular-nanophotonics
Enter your password:
Uploading distributions to https://upload.pypi.org/legacy/
Uploading mypackage-0.0.1-py3-none-any.whl
100%|█████████████████████████████████████| 
Uploading mypackage-0.0.1.tar.gz
100%|█████████████████████████████████████| 

View at:
https://pypi.org/project/mypackage/0.0.1/
```

You can use `pip` to install your package and verify that it works. 
