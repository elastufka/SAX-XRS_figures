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

<img src="https://github.com/elastufka/SAX-XRS_figures/blob/gh-pages/images/DEXTR%20Image%20Segmentation%20test%20with%20HMI%20data/hero.png?raw=true">

With this simple and clear object shape, even the network trained on non-scientific, photographic images performs well.

<img src="https://github.com/elastufka/SAX-XRS_figures/blob/gh-pages/images/DEXTR%20Image%20Segmentation%20test%20with%20HMI%20data/input3.png?raw=true">

Multiple object segmentation example with two sunspots in a sunspot group.


##  Pre-trained model applied to AIA data

<img src="https://github.com/elastufka/SAX-XRS_figures/blob/gh-pages/images/DEXTR%20Image%20Segmentation%20test%20with%20HMI%20data/input2.png?raw=true">

AIA 304 image - defining the extreme points of what looks like a darker band of plasma overlying a brighter area performs decently, although details of finer structure are lost.


## Possible applications

This could be a good candidate for transfer learning, with the goal of solar image segmentation in mind. 

The most suitable dataset that comes to mind is coronal holes; they are large, irregularly shaped but continuous, and their exact bounding polygons are available from HEK results. For multi-class segmentation (flares, sigmoids, jets, etc), much more pre-processing and data labelling would need to be done.

An interesting application could be for EUV flare ribbon finding. Perhaps this method could perform better than basic thresholding?

Challenges:
- It seems like the object must be continuous. Therefore, sunspots in a group have to be treated individually
- Extreme pixels must be located on the object or boundaries of the object. Loosely defining a bounding box (such is the ones that are returned for sunspots from HEK queries) won't produce the desired result. However, there seem to be similar image segmentation techniques based on bounding boxes.
- The model assumes RGB image data. The input layer would have to be adjusted to single-channel (or one channel per wavelength if using a full AIA/HMI image cube) to accomodate scientific image data and remove dependency on a colorscale. Depending on image saturation/contrast, this could make determining the extreme points by eye less reliable however. Automated finding of extreme points via contour levels might be a good alternative, for features like sunspots and perhaps even loops (probably not sigmoids though).




