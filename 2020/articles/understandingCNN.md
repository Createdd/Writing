# Understanding Neural Style Transfer with CNNs better

![]()

Today I want to talk about CNNs used in Neural Style Transfer. There are already quite a few articles and tutorials available. Sometimes some content is just copied, some provide novel implementation. What all have in common is a very fast dive into specifics. Too specific in my opinion. Not only that, but there are often implementation details that make it harder to focus on the main concept as a whole.

This article can be considered as an overview and comprehension of other articles (listed in my "Inspiration" section), to understand the concept on a higher level. My intention is to strip away some implemenation details, but being high level enough for beginners (snd sparking curiosity for the original research paper and subsequent implementations).

## Table of Contents

- [Understanding Neural Style Transfer with CNNs better](#understanding-neural-style-transfer-with-cnns-better)
  - [Table of Contents](#table-of-contents)
- [Disclaimer](#disclaimer)
  - [Requirements](#requirements)
  - [Neural Style Transfer](#neural-style-transfer)
  - [Architectural and process overview](#architectural-and-process-overview)
  - [Transfer learning and style transfer](#transfer-learning-and-style-transfer)
    - [1. Transfer learning](#1-transfer-learning)
    - [2. Style Transfer](#2-style-transfer)
  - [Style and content](#style-and-content)
  - [Loss calculation](#loss-calculation)
    - [Content cost](#content-cost)
    - [Style cost](#style-cost)
    - [Total variation cost](#total-variation-cost)
  - [Starting point for implementation](#starting-point-for-implementation)
  - [Inspriation](#inspriation)
  - [Appendix](#appendix)
    - [Content cost](#content-cost-1)
  - [About](#about)

# Disclaimer

I am not associated with any of the services I use in this article.

I do not consider myself an expert. If you have the feeling that I am missing important steps or neglected something, consider pointing it out in the comment section or get in touch with me.

I am always happy for constructive input and how to improve.


This was written on XXXXXXXDATEXXXXXXXXXX.
I cannot monitor all my articles. There is a high probability that, when you read this article the tipps are outdated and the processes have changed.

If you need more information on certain parts, feel free to point it out in the comments.

## Requirements

Even though I want to explain everything from the ground, I assume understanding of **convolutional neural networks (CNNs)**. The principle concept is very crucial for many things in computer vision and deep learning. There are many resources online available. As a refresher, I suggest this [article](https://medium.com/@himadrisankarchatterjee/a-basic-introduction-to-convolutional-neural-network-8e39019b27c4)

## Neural Style Transfer

> In fine art, especially painting, humans have mastered the skill to create unique visual experiences through composing a complex interplay between the content and style of an image. Thus far the algorithmic basis of this process is unknown and there exists no artificial system with similar capabilities. However, in other key areas of visual perception such as object and face recognition near-human performance was recently demonstrated by a class of biologically inspired vision models called Deep Neural Networks. Here we introduce an artificial system based on a Deep Neural Network that creates artistic images of high perceptual quality.

Research paper [A Neural Algorithm of Artistic Style](https://arxiv.org/pdf/1508.06576.pdf) - by Leon A. Gatys, Alexander S. Ecker, Matthias Bethge

> The system uses neural representations to separate and recombine content and style of arbitrary images, providing a neural algorithm for the creation of artistic images. Moreover, in light of the striking similarities between performance-optimised artificial neural networks and biological vision, our work offers a path forward to an algorithmic understanding of how humans create and perceive artistic imagery.

## Architectural and process overview

There are many good visualizations on how the cnn works with neural style transfer.
I wanted to draw it myself, but then I realised that there are already very nice ones available. So I will just show those and reference the creators for credit.

The following I consider to be fantastic.


First this one. It shows very beautifully how the loss is calculated, and how it fits together in the overall result.

![](../assets/understandingCNN_2020-10-09-22-29-08.png)

from his [blog](https://www.mikegao.net/graphics/summary/neural_style.html) und the [creative commons licnece](https://creativecommons.org/licenses/by-nc/4.0/)

This one is also good. Showing the reconstructions development over the different layers.

![](../assets/understandingCNN_2020-10-10-10-10-17.png)
from the [original research paper](https://arxiv.org/pdf/1508.06576.pdf) under [arxiv licenses requirements](https://arxiv.org/help/license)


It is necessary to say what the different layers of a CNN represent in order to understand the subsquent calculations.

- The shallower layers of a CNN tend to detect lower-level features such as edges and simple textures.
- The deeper layers tend to detect higher-level features such as more complex textures as well as object classes.

As the generated image shall have similar content as the input image. It is advisable to use a layer in the middle, representing content to a high degree.

![](../assets/understandingCNN_2020-10-16-15-29-00.png)

VGG19 architecture from research paper [Automatic Mass Detection in Breast Using Deep Convolutional Neural Network and SVM Classifier](https://www.researchgate.net/publication/334388209_Automatic_Mass_Detection_in_Breast_Using_Deep_Convolutional_Neural_Network_and_SVM_Classifier) und the [creative commons licnece](https://creativecommons.org/licenses/by/4.0/)

## Transfer learning and style transfer

Another important concept is that a pre-trained network is used. Most often VGG-19. It is noteworthy that we make use of so called "transfer learning".

We have 2 concepts here to distinguish:
1. Transfer learning
2. Style transfer

Though, both use the word "transfer" they are quite different from an implementation standpoint.

### 1. Transfer learning

The concept itself is extremely interesting and potent to create new solutions by the use of established models.

I do not want to expand on this concept in this article. For a fantastic introduction I can recommend this article: https://machinelearningmastery.com/transfer-learning-for-deep-learning/. However, it is crucial to understand how it is used in the concept of style transfer.

In short we can say
> Transfer learning and domain adaptation refer to the situation where what has been learned in one setting … is exploited to improve generalization in another setting

This is especially useful in computer vision, as the computation and training of those models are quite resource hungry. Using a model that has been trained on a huge dataset, where the result is now freely available is actually very nice for inidvidual experimentation.

You can use transfer learning as:
1. direct use of a pre-trained model
2. feature extraction of pre-trained models
3. changing weights of the last layer of a pre-trained model

In our case we will use the second approach. Using feature extraction, where, the output of the model from a layer prior to the output layer is used as input for a new classifier.



### 2. Style Transfer

From the original paper:

> Conceptually most closely related are methods using texture transfer to achieve artistic style transfer. However, these previous approaches mainly rely on non-parametric techniques to directly manipulate the pixel representation of an image. In contrast, by using Deep Neural Networks trained on object recognition, we carry out manipulations in feature spaces that explicitly represent the high level content of an image.

So this means that the spcialty of the deep learning approach is to extract the style of an image not with mere pixel observation of the style picture, but rather the extracted features of the pre-trained model combined with the content of the style image. So, in essence, to discover the style of an image, we
1. process the style image by analyzing its pixels
2. feeding this information to the layer of a pre-trained model to "understand"/classify the provided input as objects

How this is done we will explore in the section "style cost".

## Style and content

The basic idea is to transfer the style of an image on the content of an image.

Therefore we need to understand two things:
1. What is the content of an image
2. What is the style of an image

Loosely speaking the content of an image is what we humans identify as objects in an image. A car, a bridge, houses, etc.
Style is a harder to define. It heavily depends on the image. It is overall texture, color selection, contrast, etc.

Those definitions need to be expressed in a mathematical way to be implemented in the world of machine learning.


## Loss calculation

As we can see the central element for this process is the loss calculation. There are 3 costs that need to be caluclated:

1. Content cost
2. Style cost
3. Total (variation) cost

Those steps are in my opinion the hardest to understand, so lets dive into it one by one.

### Content cost

What is content cost?

As we found out before, we define the content of an image by its objects. Things that we as humans can recognize as things.

Having understood the structure of a CNN, it now becomes apaprent that at the end of the neural network we can access a layer, that represents the objects (the content) quite well. Going through the pooling layers we lose the stylistic parts of the image, but in terms of getting the content this is desired.

Now the feature maps in higher layers of the CNN are activated in the presence of different objects. So if two images to have the same content, they should have similar activations in the higher layers.

That is the premise for defining the cost function.


The following image helps to understand how the layer is rolled out to be prepared for calculations (which are not covered in this article):

![](../assets/understandingCNN_2020-10-10-10-24-54.png)
from [Aditya Guptas article](https://github.com/Adi-iitd/AI-Art) under [MIT License](https://github.com/Adi-iitd/AI-Art/blob/add-license-1/LICENSE)



### Style cost


Again, make sure to understand the difference between style of an image and style loss of an image.. Both calculations are different. One is to detect the "style representation" (texture, colors, etc), the other is to compare the style of the original image with the style of the generated image.

The novel idea here is to identify style of an image. This is done by
1. Getting the feature vectors from a convolutional layer
2. Comparing those vectors with feature vectors from another layer (finding its correlation)



The correlation is captuered by multiplying the feature map to its transpose, resulting in the gram matrix.

![](../assets/understandingCNN_2020-10-10-11-34-54.png)
from [Aditya Guptas article](https://github.com/Adi-iitd/AI-Art) under [MIT License](https://github.com/Adi-iitd/AI-Art/blob/add-license-1/LICENSE)

Luckily the CNN provides us with multiple layers we can choose of to find its styles correctly. Comparing various layers and its correlations we can identify the style of an image.

Comparing this style with the style


The cost is the difference between those gram matrices, ie the difference of correlations.

### Total variation cost

It acts like a regularizer that encourages spatial smoothness in the generated image.
This was not used in the original paper but sometimes improves the results.


## Starting point for implementation

We will start with the tutorial from [Keras](https://keras.io/examples/generative/neural_style_transfer/).

- Github Source: https://github.com/keras-team/keras-io/blob/master/examples/generative/neural_style_transfer.py
- License: https://github.com/keras-team/keras-io/blob/master/LICENSE

Gist: https://gist.github.com/Createdd/2fa6fa0770135a34a8f1f022007dda69




## Inspriation

Absolutely great work by Thushan Ganegedara in his article: https://towardsdatascience.com/light-on-math-machine-learning-intuitive-guide-to-neural-style-transfer-ef88e46697ee

- https://www.mikegao.net/graphics/summary/neural_style.html by [Mike Gao](https://www.mikegao.net/)
- https://medium.com/tensorflow/neural-style-transfer-creating-art-with-deep-learning-using-tf-keras-and-eager-execution-7d541ac31398 original tutorial from tensorflow
- https://machinelearningmastery.com/transfer-learning-for-deep-learning/
- https://machinelearningmastery.com/how-to-use-transfer-learning-when-developing-convolutional-neural-network-models/
- https://towardsdatascience.com/what-is-deep-transfer-learning-and-why-is-it-becoming-so-popular-91acdcc2717a
- https://arxiv.org/pdf/1701.01036.pdf Demystifying Neural Style Transfer
- https://towardsdatascience.com/neural-networks-intuitions-2-dot-product-gram-matrix-and-neural-style-transfer-5d39653e7916
- https://github.com/aleju/papers/blob/master/neural-nets/A_Neural_Algorithm_for_Artistic_Style.md summary of publication paper
- https://towardsdatascience.com/art-with-ai-neural-style-transfer-63d0ef76596a


Implementations with code:

- https://towardsdatascience.com/neural-style-transfer-4d7c8138e7f6
- http://ziqingguan.net/index.php/2020/05/30/deep-learning-art-neural-style-transfer/

## Appendix

I put formulas in this section. I wanted to keep the article quite basic. Providing the formulas sparks avoidance in some people and for the purpose of my article they are not necessary. Nevertheless I put some thoughts to it as you can see in the following lines.

### Content cost


The formula represents that as:

![](../assets/understandingCNN_2020-10-10-10-16-57.png)
from the [original research paper](https://arxiv.org/pdf/1508.06576.pdf) under [arxiv licenses requirements](https://arxiv.org/help/license)

> where F is the activation of the i th filter at position j in layer l.
> So let ~p and ~x be the original image and the image that is generated and P l and F l their respective feature representation in layer l.

it is in fact just the root mean squared error between the feature representation of the generated image and the content image.


The question is how we get the feature representation?

![](../assets/understandingCNN_2020-10-10-10-38-35.png)
from the [original research paper](https://arxiv.org/pdf/1508.06576.pdf) under [arxiv licenses requirements](https://arxiv.org/help/license)

> This is done by minimising the mean-squared distance between the entries of the Gram matrix from the original image and the Gram matrix of the image to be generated

> Gl ij is the inner product between the vectorised feature map i and j in layer l:
> So let ~a and ~x be the original image and the image that is generated and Al and Gl their respective style representations in layer l.
> A layer with Nl distinct filters has Nl feature maps each of size Ml , where Ml is the height times the width of the feature map


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