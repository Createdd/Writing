# Understanding Neural Style Transfer with CNNs better

![]()

Today I want to talk about CNNs used in Neural Style Transfer. There are great tutorials available online. However, I struggle sometimes with grasping the main concepts. The reason for that is that there are always different implementation details.

This article can be considered as an overview and comprehension of other articles (listed in my "Inspiration" section), to understand the concept on a higher level. My intention is to strip away some implemenation details, but being high level enough for beginners. (And sparking curiosity for the original research paper and subsequent implementations)

## Table of Contents

- [Understanding Neural Style Transfer with CNNs better](#understanding-neural-style-transfer-with-cnns-better)
  - [Table of Contents](#table-of-contents)
- [Disclaimer](#disclaimer)
  - [Neural Style Transfer](#neural-style-transfer)
  - [Overview on how it works](#overview-on-how-it-works)
  - [Starting point for implementation](#starting-point-for-implementation)
  - [Inspriation](#inspriation)
  - [About](#about)

# Disclaimer

I am not associated with any of the services I use in this article.

I do not consider myself an expert. If you have the feeling that I am missing important steps or neglected something, consider pointing it out in the comment section or get in touch with me.

I am always happy for constructive input and how to improve.


This was written on XXXXXXXDATEXXXXXXXXXX.
I cannot monitor all my articles. There is a high probability that, when you read this article the tipps are outdated and the processes have changed.

If you need more information on certain parts, feel free to point it out in the comments.

## Neural Style Transfer

> In fine art, especially painting, humans have mastered the skill to create unique visual experiences through composing a complex interplay between the content and style of an image. Thus far the algorithmic basis of this process is unknown and there exists no artificial system with similar capabilities. However, in other key areas of visual perception such as object and face recognition near-human performance was recently demonstrated by a class of biologically inspired vision models called Deep Neural Networks. Here we introduce an artificial system based on a Deep Neural Network that creates artistic images of high perceptual quality.

Research paper [A Neural Algorithm of Artistic Style](https://arxiv.org/pdf/1508.06576.pdf) - by Leon A. Gatys, Alexander S. Ecker, Matthias Bethge

> The system uses neural representations to separate and recombine content and style of arbitrary images, providing a neural algorithm for the creation of artistic images. Moreover, in light of the striking similarities between performance-optimised artificial neural networks and biological vision, our work offers a path forward to an algorithmic understanding of how humans create and perceive artistic imagery.

## Overview on how it works

There are many good visualizations on how the cnn works with neural style transfer.
I wanted to draw it myself, but then I realised that there are already very nice ones available. So I will just show those and reference the creators for credit.

The following I consider to be fantastic:


![](../assets/understandingCNN_2020-10-09-22-29-08.png)

from his [blog](https://www.mikegao.net/graphics/summary/neural_style.html) und the [creative commons licnece](https://creativecommons.org/licenses/by-nc/4.0/)



## Starting point for implementation

We will start with the tutorial from [Keras](https://keras.io/examples/generative/neural_style_transfer/).

- Github Source: https://github.com/keras-team/keras-io/blob/master/examples/generative/neural_style_transfer.py
- License: https://github.com/keras-team/keras-io/blob/master/LICENSE

Gist: https://gist.github.com/Createdd/2fa6fa0770135a34a8f1f022007dda69




## Inspriation

Absolutely great work by Thushan Ganegedara in his article: https://towardsdatascience.com/light-on-math-machine-learning-intuitive-guide-to-neural-style-transfer-ef88e46697ee

- https://www.mikegao.net/graphics/summary/neural_style.html by [Mike Gao](https://www.mikegao.net/)
- https://medium.com/tensorflow/neural-style-transfer-creating-art-with-deep-learning-using-tf-keras-and-eager-execution-7d541ac31398 original tutorial from tensorflow


---

## About

Daniel is an entrepreneur, software developer, and business law graduate. He has worked at various IT companies, tax advisory, management consulting, and at the Austrian court.

His knowledge and interests currently revolve around programming machine learning applications and all its related aspects. To the core, he considers himself a problem solver of complex environments, which is reflected in his various projects.

Don't hesitate to get in touch if you have ideas, projects, or problems.

![You can support me on https://www.buymeacoffee.com/createdd](/2020/assets/template_2020-09-25-22-32-52.png)
You can support me on https://www.buymeacoffee.com/createdd

![picture of myself](https://avatars2.githubusercontent.com/u/22077628?s=460&v=4)

**Connect on:**
- [LinkedIn](https://www.linkedin.com/in/createdd)
- [Github](https://github.com/Createdd)
- [Medium](https://medium.com/@createdd)
- [Twitter](https://twitter.com/_createdd)
- [Instagram](https://www.instagram.com/create.dd/)
- [createdd.com](https://www.createdd.com/)

<!-- Written by Daniel Deutsch -->