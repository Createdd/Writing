# Law and Statistics - A beginner example using TensorFlow
[<img src="https://images.unsplash.com/photo-1530278761482-a352c8e3192c?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=70c20f6eb1e412c2ae298211e04cef2f&auto=format&fit=crop&w=2764&q=80">](
https://unsplash.com/photos/bD5lzOBx-Cs)
Photo by Steve Roe on Unsplash - https://unsplash.com/photos/bD5lzOBx-Cs


<!-- TOC -->

- [Law and Statistics - A beginner example using TensorFlow](#law-and-statistics---a-beginner-example-using-tensorflow)
  - [Get started](#get-started)
    - [Shell commands for installing everything you need](#shell-commands-for-installing-everything-you-need)
  - [Get data and draw a plot](#get-data-and-draw-a-plot)
    - [Import everything you need](#import-everything-you-need)
    - [Create and plot some numbers](#create-and-plot-some-numbers)
  - [Build a TensorFlow model](#build-a-tensorflow-model)
    - [Prepare data](#prepare-data)
    - [](#)

<!-- /TOC -->

---

## Get started

Install TensorFlow with virtualenv. See the [guide](https://www.tensorflow.org/install/install_mac) on the TF website.

### Shell commands for installing everything you need

```shell
sudo easy_install pip

pip3 install --upgrade virtualenv 

virtualenv --system-site-packages <targetDirectory>

cd <targetDirectory>

source ./bin/activate 

easy_install -U pip3

pip3 install tensorflow 

pip3 install matplotlib

```
## Get data and draw a plot

### Import everything you need

```python
import tensorflow as tf
import numpy as np
import math
import matplotlib  
matplotlib.use('TkAgg')   
import matplotlib.pyplot as plt  
import matplotlib.animation as animation
```

### Create and plot some numbers

```python
## Generate evidence numbers between 10 and 20
np.random.seed(42)
num_evid = np.random.randint(low=10, high=50, size=80)

# Generate number of convictions from the evidence with a random noise added
num_convict = num_evid + np.random.randint(low=3, high=10, size=80)

print(num_evid)
print(num_convict)

# Plot the numbers
plt.title('Number of convictions based on evidence')
plt.plot(num_evid, num_convict, "bx") # bx = blue x
plt.xlabel("Number of Evidence")
plt.ylabel("Number of Convictions")
plt.show()
```

## Build a TensorFlow model 

To build a basic machine learning model, we need to prepare the data, make predictions, measure the loss and optimize by minimizing the loss.

### Prepare data

```python
# normalize values
def normalize(array):
  return (array - array.mean()) / array.std()

# use 70% of the data for training (the remaining 30% shall be used for testing)
numTrain = math.floor(sampleSize * 0.7)

# convert list to an array 

trainEvid = np.asanyarray(numEvid[:numTrain])
trainConvict = np.asanyarray(numConvict[:numTrain])

# normalize arrays
trainEvidNorm = normalize(trainEvid)
trainConvictdNorm = normalize(trainConvict)
```

### 

Use "feeding" as it, lets you inject data into any Tensor in a computation graph. More in reading data [here](https://www.tensorflow.org/api_guides/python/reading_data#Feeding).


```python

```
```python

```
```python

```
```python

```

---

Thanks for reading my article! Feel free to leave any feedback! 

---

Daniel is a LL.M. student in business law, working as a software engineer and organizer of tech related events in Vienna. 
His current personal learning efforts focus on machine learning. 

Connect on:
- [LinkedIn](https://www.linkedin.com/in/createdd) 
- [Github](https://github.com/Createdd)
- [Medium](https://medium.com/@ddcreationstudi)
- [Twitter](https://twitter.com/DDCreationStudi)
- [Steemit](https://steemit.com/@createdd)
- [Hashnode](https://hashnode.com/@DDCreationStudio)

<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->