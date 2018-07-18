# Deep Learning Model Step by Step

[<img src="https://images.unsplash.com/photo-1486848538113-ce1a4923fbc5?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=57d5ed3770de4f9b039e5a3e54403ebe&auto=format&fit=crop&w=1287&q=80">](https://unsplash.com/photos/mBHuEkka5wM)
Photo by Adrien Ledoux on Unsplash - https://unsplash.com/photos/mBHuEkka5wM

This article serves as a reminder for me on how to (generally) approach a supervised deep learning architecture with Python.

## Table of Contents

- [Deep Learning Model Step by Step](#deep-learning-model-step-by-step)
	- [Table of Contents](#table-of-contents)
	- [General Implementation Workflow](#general-implementation-workflow)
	- [Initial Initialization Of Parameters](#initial-initialization-of-parameters)
	- [Forward propagation](#forward-propagation)

## General Implementation Workflow

Number of layers = L

1.  Initialize parameters and define hyperparameters
2.  Loop:
    a. Forward propagation
    b. Compute cost
    c. Backward propagation
    d. Update parameters (using parameters, and grads from backward propagation)
3.  Use trained parameters to predict labels
4.  Test predictions on examples

## Initial Initialization Of Parameters

```python
for l in range(1, L):
	parameters['W' + str(l)] = np.random.randn(layer_dims[l], layer_dims[l-1]) * 0.01
	parameters['b' + str(l)] = np.zeros((layer_dims[l], 1))
```

## Forward propagation

Define variables according to the formula:

Z[l]=W[l]A[l−1]+b[l

Whereas

- Z is the input of the activation function
- cache containing "A", "W" and "b" - for computing the backward propagation

```python
def linear_forward(A, W, b)
    Z = np.dot(W,A)+b
    cache = (A, W, b)

		return Z, cache
```

```python
def linear_activation_forward(A_prev, W, b, activation="relu/sigmoid"):
		# Sigmopid activation
		Z, linear_cache = linear_forward(A_prev, W, b)
		A, activation_cache = sigmoid(Z)

		# Relu activation
		Z, linear_cache = linear_forward(A_prev, W, b)
		A, activation_cache = relu(Z)

		return A, cache
```

```python
def L_model_forward(X, parameters):
    for l in range(1, L):
        A_prev = A
        A, cache = linear_activation_forward(A_prev,parameters["W"+ str(l)],parameters["b"+ str(l)], activation = "relu")
        caches.append(cache)

    AL, cache = linear_activation_forward(A, parameters["W"+ str(L)],parameters["b"+ str(L)], activation = "sigmoid")
    caches.append(cache)

    return AL, caches

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
