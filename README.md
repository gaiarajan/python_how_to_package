# How to package a Python project

PyPI is the Python package index. Repositories in PyPI can be installed using `pip`, the Python package manager. To post code to the PyPI repository, take the following steps:

## Create a LICENSE
Without a license, no one can replicate or modify your code.  For an open source project, this is non-ideal.  Common licenses used for code include the MIT License (short and permissive), and the GNU GPLv3, which stops people from producing closed-source software from your work.

To add a LICENSE, add a file named LICENSE and then choose from GitHub's options on the right.  Then commit to save your work.

## Create a README
Make sure it's descriptive, and includes instructions for possible installation. Contributors will appreciate having this easy, accessible introduction to your project, goals, and possible future directions. 

Here's a [great checklist](https://github.com/ddbeck/readme-checklist/blob/main/checklist.md) for READMEs! 
## Create a build script (setup.py)

setup.py is the build script for setuptools. It tells setuptools about your package (such as the name and version) as well as which code files to include. Your setup.py file is what describes your package, and tells setuptools how to package, build and install it.

## Generate a distribution package
Check your installation of `setuptools` and `wheel`:

    pip install --user --upgrade setuptools wheel

Then, run the command below in the same directory as `setup.py`:

    python3 setup.py sdist bdist_wheel
    
This should output a lot of text, then will create two files in the `dist` directory. 

## Upload your package

Register an account on `PyPI` and verify your email. Then create a PyPI API token in your [account settings](https://pypi.org/manage/account/). Make sure to keep open the page with your token or save it somewhere because you'll need it later in this step! Then, you can upload your package via Twine, and install Twine using this command:

    pip install --user --upgrade twine
    
Then run Twine to upload.
    
    python3 -m twine upload dist/*

When prompted, enter your credentials, using `__token__` as your username and your API token as the password. Your package should then be visible on PyPI!

## Installing your newly uploaded package

To install your package and verify that it works user can use pip. Install your package from PyPI:

    -m pip install --index-url  --no-deps example-pkg-YOUR-USERNAME-HERE
    
Make sure to specify your username in the package name!

pip will install the package. You can test that it was installed correctly by importing the package. 


**Written for CSC630 in fall 2020 by Sarah, Gaia, Nikol, and Ali**

**Adapted from [python.org](https://packaging.python.org/tutorials/packaging-projects/)**
