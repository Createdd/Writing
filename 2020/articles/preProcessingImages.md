# Preprocessing your images for machine learning

![https://images.unsplash.com/photo-1515401558980-f84ec141ebf9?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2250&q=80](https://images.unsplash.com/photo-1515401558980-f84ec141ebf9?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2250&q=80)
Photo by Jye B on Unsplash - https://unsplash.com/photos/RuTMP0iI_ek

During my studies at [JKU](https://www.jku.at/en/degree-programs/types-of-degree-programs/bachelors-and-diploma-degree-programs/ba-artificial-intelligence/) there was a task for preprocessing images for a machine learning project. It is necessary to clean the raw images before using them in a learning algorithm, so thats why we create a pre-processing function. I think it can be quite useful for others as well so I want to share a bit of my approach.

## Table of Contents

- [Preprocessing your images for machine learning](#preprocessing-your-images-for-machine-learning)
  - [Table of Contents](#table-of-contents)
  - [The pre processing errors](#the-pre-processing-errors)
  - [The processing file](#the-processing-file)
  - [Python code](#python-code)
  - [About](#about)

## The pre processing errors

There are a few errors, that are often encountered when processing images for machine learning tasks. Those are the following:

1. The correct file extension, representing an image file (e.g. jpg)
2. A certain file size
3. The file can be read as an image (depending on the library that is used for further processing)
4. The image data has useable information (more than just one value)
5. The image has a certain width and height
6. There are no duplicate images

## The processing file

The function takes 3 arguments:
1. the input_directory, which contains the image files
2. the output_directory, where the valid images shall be copied
3. a logfile containing the errors

My solution searches recursively for the allowed image files. This is done by the `get_files` function.

The `check_files` function gets the files and returns the list of images with a corresponding error code.

The `validate_file` function checks the images for the various common errors and returns the number of the error. If no error occurred, the error code will be 0.


The `separate_files` function will divide the valid and the invalid images.

The `copy_valid_files` function will copy the valid files into the defined "output_dir" folder.

The `write_log_file` function creates a logfile in the specified logfile path, containing all files that have errors.

The whole `pre_processing` function ultimately returns the number of valid files.

## Python code

The python file can be found in my Data Science Collection repository: [https://github.com/Createdd/DataScienceCollection](https://github.com/Createdd/DataScienceCollection)

Here you can inspect the code via Github Gist:

https://gist.github.com/Createdd/f190b1511678f89a36ffaf426a07462d








---

## About

Daniel is an entrepreneur, software developer, and lawyer.
His knowledge and interests evolve around business law and programming machine learning applications.
To the core, he considers himself a problem solver of complex environments, which is reflected in his various projects.
Don't hesitate to get in touch if you have ideas, projects or problems.

![picture of myself](https://avatars2.githubusercontent.com/u/22077628?s=460&v=4)

**Connect on:**
- [LinkedIn](https://www.linkedin.com/in/createdd)
- [Github](https://github.com/Createdd)
- [Medium](https://medium.com/@createdd)
- [Twitter](https://twitter.com/_createdd)
- [Instagram](https://www.instagram.com/create.dd/)


<!-- Written by Daniel Deutsch -->