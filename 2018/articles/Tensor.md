# Tensorflow Series - Tensors in simple

[<img src="https://images.unsplash.com/photo-1505870493536-5349bcc99cb1?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=d73d25857678672c1958bc1319b96e0e&auto=format&fit=crop&w=2250&q=80">](
https://unsplash.com/photos/rbRa_Gs_mb0)
Photo by Sunyu on Unsplash - https://unsplash.com/photos/rbRa_Gs_mb0

Exploring Tensorflow brings me to the first question. What is a Tensor and why is the library called Tensorflow?
I will try to focus on the very most important concepts to make it as easy to understand as possible.
Let's see!

## 

As the developers put it on their [website](https://www.tensorflow.org/programmers_guide/tensors): 

> TensorFlow, as the name indicates, is a framework to define and run computations involving tensors. A tensor is a generalization of vectors and matrices to potentially higher dimensions. Internally, TensorFlow represents tensors as n-dimensional arrays of base datatypes.

A TensorFlow Core program basically 2 things:
1. Building a computational graph 
1. Running a computational graph

### Computational graph

A computational graph is a "series of TensorFlow operations arranged into a graph". 
This graph can have 2 types of objects:
1. Operations (or "ops"): The nodes of the graph. Operations describe calculations that consume and produce tensors.
1. Tensors: The edges in the graph. These represent the values that will flow through the graph.

Basically tensors are n-dimensional arrays. Those arrays shall flow between operations. 

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