---
title: "DEXTR Image Segmentation test with HMI data"
image: 
  path: /images/transparent_banner.png
  thumbnail: /images/DEXTR Image Segmentation test with HMI data/hero.png
  caption:
categories:
  - posts
tags:
  - HMI
  - AIA
  - deep learning
  - image segmentation
  - computer vision
---

Deep Extreme Cut [DEXTR](https://github.com/scaelles/DEXTR-PyTorch) uses extreme points of an object in an image as input to perform image segmentation. Here are some results of using the model trained on PASCAL VOC to segment HMI and AIA images (after conversion to RGB jpg).
    
##  Pre-trained model applied to HMI data

<img src="">

With this simple and clear object shape, even the network trained on non-scientific, photographic images performs well.

##  Pre-trained model applied to AIA data

<img src="">

<img src="">


## Possible applications

This could be a good candidate for transfer learning, with the goal of solar image segmentation in mind. 

The most suitable dataset that comes to mind is coronal holes; they are large, irregularly shaped but continuous, and their exact bounding polygons are available from HEK results. For multi-class segmentation (flares, sigmoids, jets, etc), much more pre-processing and data labelling would need to be done.

Challenges:
- It seems like the object must be continuous. Therefore, sunspots in a group have to be treated individually
- Extreme pixels must be located on the object or boundaries of the object. Loosely defining a bounding box (such is the ones that are returned for sunspots from HEK queries) won't produce the desired result. However, there seem to be similar image segmentation techniques based on bounding boxes.
- The model assumes RGB image data. The input layer would have to be adjusted to single-channel (or one channel per wavelength if using a full AIA/HMI image cube) to accomodate scientific image data




