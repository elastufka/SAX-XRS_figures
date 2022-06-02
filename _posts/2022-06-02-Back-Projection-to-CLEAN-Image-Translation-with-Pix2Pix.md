---
title: "Back Projection to CLEAN Image Translation with Pix2Pix"
image: 
  path: /images/transparent_banner.png
  thumbnail: /images/Back Projection to CLEAN Image Translation with Pix2Pix/hero.png
  caption:
categories:
  - posts
tags:
  - deep learning
  - computer vision
  - STIX
---

Image-to-image translation has been sucessfully demonstrated for many cases, such as colorizing black-and-white images or filling in an object from its edges. [Tensorflow](https://www.tensorflow.org/tutorials/generative/pix2pix#training) has a detailed tutorial using Isola et al's [Pix2Pix](https://arxiv.org/abs/1611.07004). It uses a generator with a U-Net-based architecture and a discriminator using a convolutional PatchGAN classifier.

Such a method should be successful in translating STIX back-projection images to CLEAN images. Fourier Backprojection simply projects visibilities into image space, and is itself the starting point of the CLEAN algorithm; it is the "dirty map". While Backprojection is fast, CLEAN can take quite some time to converge, and is usually run for at least 100 iterations. Especially for the case of preview images, image translation could be a viable method to decrease server loads while providing reasonable first-look results.

Image pairs were prepared using the STIX preview image archive, containing ~ 2700 images in the 4-10 keV range. Only images with the default 60s integration time were considered. Images in pairs also needed to have the same CRPIX coordinates, to ensure that the image pairs were centered on the same solar location. CLEAN images needed to be cropped from their generated size of (257,257) to match the Backprojection image size of (256,256), in such a way that the solar location was accurately preserved. Then the image data arrays were exposure normalized and then normalized according to the ranges of values in each dataset. This was to ensure that low-flux images could be distinguished from high-flux images. 

A training set of ~1700 image pairs was the result. Training for 35K epochs resulted in a low L1 loss and reasonable losses for both the generator and discriminator. Some examples of the inputs and predictions are shown below. Image translation notably struggles in the case of multiple sources; this could however be due to an imbalance in the dataset.

![example1](https://github.com/elastufka/SAX-XRS_figures/blob/gh-pages/images/Back%20Projection%20to%20CLEAN%20Image%20Translation%20with%20Pix2Pix/example1.png?raw=true)

![example1](https://github.com/elastufka/SAX-XRS_figures/blob/gh-pages/images/Back%20Projection%20to%20CLEAN%20Image%20Translation%20with%20Pix2Pix/example2.png?raw=true)

![example1](https://github.com/elastufka/SAX-XRS_figures/blob/gh-pages/images/Back%20Projection%20to%20CLEAN%20Image%20Translation%20with%20Pix2Pix/example3.png?raw=true)


