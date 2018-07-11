# Debugging TensorFlow - A starter

[<img src="https://images.unsplash.com/photo-1496737018672-b1a6be2e949c?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=f0aa3d84be0ad9a656a27a318f055ee9&auto=format&fit=crop&w=2691&q=80">](https://unsplash.com/photos/5brvJbR1Pn8)
Photo by Matthew Kane on Unsplash - https://unsplash.com/photos/5brvJbR1Pn8

## Table of Contents

- [Debugging TensorFlow - A starter](#debugging-tensorflow---a-starter)
	- [Table of Contents](#table-of-contents)
	- [What this is about](#what-this-is-about)
	- [1. Fetch and print values within Session.run](#1-fetch-and-print-values-within-sessionrun)
	- [2. Use the tf.Print operation](#2-use-the-tfprint-operation)
	- [3. Use the Tensorboard debugger](#3-use-the-tensorboard-debugger)
	- [4. Use the TensorFlow debugger](#4-use-the-tensorflow-debugger)

## What this is about

> Debugging is twice as hard as writing the code in the first place. Therefore, if you write the code as cleverly as possible, you are, by definition, not smart enough to debug it. - BRIAN W. KERNIGHAN

Debugging in general is sometimes a tedious and challenging task. Nevertheless it is absolutely necessary to be comfortable to go through the written code and be able to identify problems.
Normally there are many guides and the process of debugging is often well documented for many languages and frameworks.

When it comes to TensorFlow however, some new challenges arise because of the way it works.

As the [official documentation](https://www.tensorflow.org/guide/low_level_intro) states:

A TensorFlow Core programs as consisting of two discrete sections:

1. Building the computational graph (a tf.Graph).
1. Running the computational graph (using a tf.Session).

![tensorsFlowing](https://www.tensorflow.org/images/tensors_flowing.gif)

The actual computation is done with `session.run()`, which means that we need to find a way to inspect values inside this function.

There are basically 3 (pragmatic) ways on how to achieve this.

As a reference I will provide my Github repository with the corresponding code.


## 1. Fetch and print values within Session.run


## 2. Use the tf.Print operation


## 3. Use the Tensorboard debugger



## 4. Use the TensorFlow debugger



Source and credit to https://www.tensorflow.org/guide/graphs

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
