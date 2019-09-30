# Working with VSCode instead of Jupyter Notebook

![https://unsplash.com/photos/JKUTrJ4vK00](https://images.unsplash.com/photo-1551288049-bebda4e38f71?ixlib=rb-1.2.1&auto=format&fit=crop&w=3300&q=80)
Photo by Luke Chesser on Unsplash


## Table of Contents

  - [Setup a local python environment](#setup-a-local-python-environment)
    - [Set a local pyenv](#set-a-local-pyenv)
    - [Installing dependencies with pipenv](#installing-dependencies-with-pipenv)
  - [Using python files with jupyter functionality](#using-python-files-with-jupyter-functionality)
  - [Converting python files and .ipynb files](#converting-python-files-and-ipynb-files)
  - [Additional: Preview a notebook in Vscode (not recommended)](#additional-preview-a-notebook-in-vscode-not-recommended)
  - [Conclusion](#conclusion)
  - [About](#about)


If you are getting started with machine learning algorithms, you will come across Jupyter Notebook. To maximize efficiency you can integrate its concept with VS Code. As this requires some understanding on how to set up a Python environment this article shall provide an introduction.

There a few reasons why it makes sense to develop you algorithms in a separate IDE. Even though jupyter notebooks are great, as soon as the code is getting more complex or the project is getting bigger, it is just not handy to have all the code in one file. VScode comes with great jupyter support and allows to transfer python code into jupyter notebook code and vice versa.


## Setup a local python environment

First you need to set up your python environment. There are many ways to organize python packages/ dependencies. It is overwhelming for a beginner.
Check out [this article](https://gioele.io/pyenv-pipenv), which explains the current standard on installing and managing python packages. Very precisely, **Gioele Barabucci** shows the following problems when installing a package:

> -Do you have enough rights to install that package? Maybe you need to use sudo pip. This sounds wrong.

> -Your application needs version 2.0 of foolib. Another Python application in you system needs version 1.8. Oops, API conflict.

> -Other people that will install your application will need foolib. You need to document it somewhere, for example in requirements.txt. But using pip freeze will record the exact version of foolib you happen to use right now. Any version of the 2.x series would be OK, but there is no easy way to tell this to pip.

> -Actually all this is moot because you need native datatypes and they are available only in Python 3.7. Unfortunately your Linux distro only ships version 3.5.


### Set a local pyenv

Install **pyenv** to manage python versions. Check out the [docs](https://github.com/pyenv/pyenv) to go through the install process.

For example you can install Python version 3.7 with `pyenv install 3.7.0`.

After setting the local python environment, you will be able to set the new python environment in VSCode:
![Gif of selecting Python Interpreter](http://g.recordit.co/tRdnrOAMHu.gif)

If you are having trouble setting up the interpreter, check out the [VScode Docs](http://recordit.co/fxFECb7aby).

### Installing dependencies with pipenv

Afterwards you can install the jupyter package with `pipenv install jupyter`.
Having selected the correct environment, you will be able to develop jupyter cells in VSCode.

## Using python files with jupyter functionality

In VSCode you can us the jupyter functionality as cells in python files. Executing the cells or running the command `Run Current File in Python Interactive window` opens an executed, notebook similar, overview:

![Run cells in VSCode](http://g.recordit.co/JM7RyyjISc.gif)

## Converting python files and .ipynb files

VSCode provides functionality to convert python files (with the jupyter markup cells) to Jupyter Notebook files. This way you can for example import a notebook as python file and run the cells as you would normally do.

![Convert notebook files and run them](http://g.recordit.co/DndtyRoXaT.gif)

See the [docs](https://code.visualstudio.com/docs/python/jupyter-support#_export-a-jupyter-notebook) for more.s


## Additional: Preview a notebook in Vscode (not recommended)

There is an extension for VSCode that allows you to display the ***.ipynb** files. It is called [VS Code Jupyter Notebook Previewer](https://marketplace.visualstudio.com/items?itemName=jithurjacob.nbpreviewer). Even though it is nice to display a full notebook rendered in VSCode, there is no functionality in editing or changing anything like we are used in a notebook. So this is simply for previewing.

![Jupyter Notebook Preview Gif](https://thumbs.gfycat.com/FarawayTerrificChameleon-max-14mb.gif)
Source from the extension [docs](https://marketplace.visualstudio.com/items?itemName=jithurjacob.nbpreviewer)

As I was using this extension it was interfering with my python extension. There was an issue that all python files were not able to reload anymore. Uninstalling this extension solved the issue again for me. See the related issue discussion [here](https://github.com/microsoft/vscode-python/issues/6392).

## Conclusion

Overall, we can see that developing jupyter-styled cells, is easy within VSCode. It allows you to use all the features the VSCode editor offers you (like [snippets](https://marketplace.visualstudio.com/items?itemName=SBSnippets.fastai-snippets)) and therefore providing a rich development experience.
Maybe it makes sense for you as well to develop in this environment, instead of just writing everything in the notebooks. ;) 

---

## About

I consider myself a problem solver. My strengths are to navigate in complex environments, provide solutions and breaking them down.
My knowledge and interests evolve around business law and programming machine learning applications.
I provide services in building data analysis and evaluating business-related concepts.

Connect on:
- [LinkedIn](https://www.linkedin.com/in/createdd)
- [Github](https://github.com/Createdd)
- [Medium](https://medium.com/@createdd)
- [Twitter](https://twitter.com/_createdd)
- [Patreon](https://www.patreon.com/createdd)

## Support and Mails

[![supportPatreon](../../patreonImg.png)](https://www.patreon.com/createdd)
https://www.patreon.com/createdd

https://upscri.be/481d76

<!-- Written by Daniel Deutsch -->