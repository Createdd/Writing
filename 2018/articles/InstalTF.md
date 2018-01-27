# Install Tensorflow on Macbook Pro 2018

[<img src="https://images.unsplash.com/photo-1508051123996-69f8caf4891d?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=288fb1a782c2813ea03f2e1e1085f853&auto=format&fit=crop&w=2251&q=80">](
https://unsplash.com/photos/_NMJqIhNpno)
Photo by Stephen Leonardi on Unsplash - https://unsplash.com/photos/_NMJqIhNpno

The more detailled guide from [Tensorflow's website](https://www.tensorflow.org/install/install_mac) broken down. I will use the [VirtuelEnv](https://virtualenv.pypa.io/en/stable/) and Python 2.7 and [zsh](http://www.zsh.org/). Enjoy!  


## Table of Contents
<!-- TOC -->

- [Install Tensorflow on Macbook Pro 2018](#install-tensorflow-on-macbook-pro-2018)
  - [Table of Contents](#table-of-contents)
  - [Installing Tensorflow](#installing-tensorflow)
    - [Shell commands](#shell-commands)
    - [Test if the installation worked](#test-if-the-installation-worked)
  - [Set up Visual Studio Code](#set-up-visual-studio-code)
    - [Set up the virtual environment](#set-up-the-virtual-environment)

<!-- /TOC -->


## Installing Tensorflow

### Shell commands

```shell
sudo easy_install pip

pip install --upgrade virtualenv 

virtualenv --system-site-packages <targetDirectory> # for python 2.7

cd <targetDirectory>

source ./bin/activate 

easy_install -U pip

pip install --upgrade tensorflow 
```

### Test if the installation worked

```shell
python

# inside the python shell
import tensorflow as tf
hello = tf.constant('Hello, TensorFlow!')
sess = tf.Session()
print(sess.run(hello))
```
This should show 'Hello, TensorFlow!' in the console.

If not, check out the [official homepage](https://www.tensorflow.org/install/install_mac#common_installation_problems) for a solution.

## Set up Visual Studio Code

- install the [Python Extension](https://marketplace.visualstudio.com/items?itemName=ms-python.python)

### Set up the virtual environment 

For more details, see the [official site](https://code.visualstudio.com/docs/python/environments#_virtual-environments).



---

Thanks for reading my article! Feel free to leave any feedback! 

---

Daniel is a LL.M. student in business law, working as a software engineer and organizer of tech related events in Vienna. 
His current personal learning efforts focus on machine learning. Connect on:
- [LinkedIn](https://www.linkedin.com/in/createdd) 
- [Github](https://github.com/DDCreationStudios)
- [Medium](https://medium.com/@ddcreationstudi)
- [Twitter](https://twitter.com/DDCreationStudi)
- [Steemit](https://steemit.com/@createdd)
- [Hashnode](https://hashnode.com/@DDCreationStudio)

<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->