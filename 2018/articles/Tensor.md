# Tensorflow Series - Tensors and the Flow
[<img src="https://images.unsplash.com/photo-1505870493536-5349bcc99cb1?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=d73d25857678672c1958bc1319b96e0e&auto=format&fit=crop&w=2250&q=80">](
https://unsplash.com/photos/rbRa_Gs_mb0)
Photo by Sunyu on Unsplash - https://unsplash.com/photos/rbRa_Gs_mb0

Exploring Tensorflow brings me to the first question. What is a Tensor and why is the library called TensorFlow?
I will try to focus on the very most important concepts to make it as easy to understand as possible.
Let's see!

I will refer to and quote only the [official documentation](https://www.tensorflow.org/programmers_guide/low_level_intro) and simplify the explanation. 

---

### Tensors and the Flow

As they put it on their [website](https://www.tensorflow.org/programmers_guide/tensors): 

> TensorFlow, as the name indicates, is a framework to define and run computations involving tensors. A tensor is a generalization of vectors and matrices to potentially higher dimensions. Internally, TensorFlow represents tensors as n-dimensional arrays of base datatypes.

### Tensor Values

> A tensor consists of a set of primitive values shaped into an array of any number of dimensions. A tensor's rank is its number of dimensions, while its shape is a tuple of integers specifying the array's length along each dimension. 

Examples:

```python
3. # a rank 0 tensor; a scalar with shape [],


[1., 2., 3.] # a rank 1 tensor; a vector with shape [3]

[ 
  [1., 2., 3.],
  [4., 5., 6.]
] # a rank 2 tensor; a matrix with shape [2, 3]

[ 
  [ 
    [1., 2., 3.]
  ],
  [ 
    [7., 8., 9.]
  ]
] # a rank 3 tensor with shape [2, 1, 3]
```

### Operations

This the "flow" part of TensorFlow. 

Operations describe calculations that consume and produce tensors.

> An Operation is a node in a TensorFlow Graph that takes zero or more Tensor objects as input, and produces zero or more Tensor objects as output.

Example:

```python
c = tf.matmul(a, b)
```

*creates an Operation of type "MatMul" that takes tensors a and b as input, and produces c as output.*

### Computational graph

A TensorFlow Core program basically 2 things:
1. Building a computational graph 
1. Running a computational graph

So what is a computational graph?

A computational graph is a "series of TensorFlow operations arranged into a graph". 
This graph can have 2 types of objects:
1. Operations: The nodes of the graph. Operations describe calculations that consume and produce tensors.
1. Tensors: The edges in the graph. These represent the values that will flow through the graph.

### Example

```python
a = tf.constant(3.0)
b = tf.constant(4.0)
total = a + b

print(a)
print(b)
print(total)
```
which will result in 

```python
Tensor("Const:0", shape=(), dtype=float32)
Tensor("Const_1:0", shape=(), dtype=float32)
Tensor("add:0", shape=(), dtype=float32)
```

These statements only build the computation graph. 
The most basic operation is a constant. The Python function that builds the operation takes a tensor value as input.

The tf.Tensor objects represent the results of the operations that will be run.
Tensors are named after the operation that produces them followed by an output index, as in "add:0" above.


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