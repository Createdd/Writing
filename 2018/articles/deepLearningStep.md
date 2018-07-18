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
  - [Compute cost](#compute-cost)
  - [Backward propagation](#backward-propagation)
  - [Updating parameters](#updating-parameters)

## General Implementation Workflow

Number of layers = L

1.  Initialize parameters and define hyperparameters
2.  Iterate over network:
  - Forward propagation
  - Compute cost
  - Backward propagation
  - Update parameters (using parameters, and grads from backward propagation)
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

## Compute cost

Formula: −1m∑i=1m(y(i)log(a[L](i))+(1−y(i))log(1−a[L](i)))


```python
def compute_cost(AL, Y):
    m = Y.shape[1]

    cost = (1./m) * (-np.dot(Y,np.log(AL).T) - np.dot(1-Y, np.log(1-AL).T))
    cost = np.squeeze(cost)

    return cost
```

## Backward propagation

Formulas:

- dW[l]=1mdZ[l]A[l−1]T
- db[l]=1m∑i=1mdZ[l](i)
- dA[l−1]=W[l]TdZ[l]


```python
def linear_backward(dZ, cache):
    A_prev, W, b = cache
    m = A_prev.shape[1]

    dW = 1./m * np.dot(dZ, A_prev.T)
    db = 1./m * np.sum(dZ, axis=1, keepdims=True)
    dA_prev = np.dot(W.T, dZ)

    return dA_prev, dW, db
```

```python
def linear_activation_backward(dA, cache, activation):
    linear_cache, activation_cache = cache

    # Relu activation
    dZ = relu_backward(dA, activation_cache)
    dA_prev, dW, db = linear_backward(dZ, linear_cache)

    # Sigmoid activation
    dZ = sigmoid_backward(dA, activation_cache)
    dA_prev, dW, db = linear_backward(dZ, linear_cache)

    return dA_prev, dW, db
```
Implement the backward function for the whole network:

```python
def L_model_backward(AL, Y, caches):
    grads = {}
    L = len(caches) # the number of layers
    m = AL.shape[1]
    Y = Y.reshape(AL.shape) # after this line, Y is the same shape as AL

    # Formula for initializing backpropagation
    dAL = dAL = - (np.divide(Y, AL) - np.divide(1 - Y, 1 - AL))

    current_cache = caches[L-1]
    grads["dA" + str(L-1)], grads["dW" + str(L)], grads["db" + str(L)] = linear_activation_backward(dAL, current_cache, activation = "sigmoid")

    for l in reversed(range(L-1)):
        current_cache = caches[l]
        dA_prev_temp, dW_temp, db_temp = linear_activation_backward(grads["dA" + str(l+1)], current_cache, activation = "relu")
        grads["dA" + str(l)] = dA_prev_temp
        grads["dW" + str(l + 1)] = dW_temp
        grads["db" + str(l + 1)] = db_temp

    return grads
```

## Updating parameters

```python
def update_parameters(parameters, grads, learning_rate):
    L = len(parameters) // 2 # number of layers in the neural network

    for l in range(L):
        parameters["W" + str(l+1)] = parameters["W" + str(l+1)] - learning_rate * grads["dW" + str(l+1)]
        parameters["b" + str(l+1)] = parameters["b" + str(l+1)] - learning_rate * grads["db" + str(l+1)]
    return parameters
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
