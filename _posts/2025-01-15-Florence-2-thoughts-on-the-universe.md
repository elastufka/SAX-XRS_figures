---
title: "Florence-2's thoughts on the universe"
image: 
  path: /images/transparent_banner.png
  thumbnail: /images/Florence2 thoughts on the universe/hero.png
  caption:
categories:
  - posts
tags:
  - deep learning
  - computer vision
  - LLM
  - MeerKAT
---

[Florence-2](https://www.microsoft.com/en-us/research/publication/florence-2-advancing-a-unified-representation-for-a-variety-of-vision-tasks/) is a vision-language foundation model developed by Microsoft, designed to handle a variety of computer vision and vision-language tasks using a unified, prompt-based approach. It's trained on a dataset that combines common image datasets like ImageNet with five billion annotations, and it seems to have some knowledge about astronomy. Here's a few examples from optical, radio, and solar images, along with some very qualitative commentary.

## Optical Galaxies (DeCAM)

![Unbarred spiral galaxy from GMNIST](https://github.com/elastufka/SAX-XRS_figures/blob/gh-pages/images/Florence2%20thoughts%20on%20the%20universe/hero.png?raw=true)

_What Florence-2 thinks:_

*CAPTION*: a spiral galaxy in the constellation ngc

*MORE_DETAILED_CAPTION*: The image is a close-up of a nebula in the constellation NGC. The nebula appears to be a spiral galaxy, with a bright blue and white coloration. It is surrounded by a dark, starry night sky, with small white stars scattered throughout. The stars are of different sizes and shapes, creating a chaotic and chaotic pattern. The image is taken from a high angle, looking up at the nebula, with the stars appearing to be slightly blurred. The overall mood of the image is dark and mysterious.

*OD*: {'bboxes': [[17.18, 17.95, 45.34, 42.01]], 'labels': ['jellyfish']}

_What I think:_

This is indeed an unbarred spiral galaxy (and not a jellyfish). If Florence had given a three word caption, it would be correct. Interestingly, the long caption contradicts the short one; it calls the galaxy a nebula, then says the nebula appears to be a galaxy. Nice to know the universe is redundantly chaotic according to AI, as well as dark and mysterious. The camera angle information is entirely irrelevant, but fine-tuning Florence to give accurate information about observation metadata could be extremely helpful.

For this one I give Florence a solid B.

![Smooth round galaxy from GMNIST](https://github.com/elastufka/SAX-XRS_figures/blob/gh-pages/images/Florence2%20thoughts%20on%20the%20universe/gmnistSR_box.png?raw=true)

_What Florence-2 thinks:_

*CAPTION*: a spiral galaxy in the constellation ngc

*MORE_DETAILED_CAPTION*: The image is a black and white photograph of a group of stars in the night sky. The stars are scattered across the sky, creating a starry background. In the center of the image, there is a bright white object, which appears to be a comet or a bright star. Surrounding the object are several smaller white stars, which are also visible in the image. The image is slightly blurred, giving it a dreamy, ethereal quality.

*OD*: {'bboxes': [[0.03, 37.92, 8.60, 50.91]], 'labels': ['street light']}

_What I think:_

This galaxy is classified as smooth and round, not a spiral. I'm guessing that there were in fact some astrophysical images in Florence-2's training data, since captions would be of the form "The galaxy NGCXXX in the constellation Orion", and the model has associated the prefix NGC with constellations. The image description isn't bad -- it's more vague and therefore less false. It's certainly not a street light, and the object detection box picks a difference source than the main galaxy.

I'd rate this performance is slightly lower than the previous, so a B-.

## Radio galaxies (VLA and MeerKAT)

![VLA Radio galaxy with extended emission](https://github.com/elastufka/SAX-XRS_figures/blob/gh-pages/images/Florence2%20thoughts%20on%20the%20universe/RGZ_attention_data2_box.png?raw=true)

_What Florence-2 thinks:_

*CAPTION*: a blue nebula with a white dot in the middle

*MORE_DETAILED_CAPTION*: The image is a square with a blue background. In the center of the square, there are two small white objects that appear to be glowing blue. The objects are curved and have a smooth texture. The background is a deep blue color, and the objects are outlined in white. The image is taken from a top-down perspective, looking down on the objects.

*OD*: {'bboxes': [[141.75, 57.36, 514.88, 427.91]], 'labels': ['picture frame']}

_What I think:_

This could have been worse, I suppose. While it identifies the two sources, it doesn't separate them via bounding box, and instead selects the whole image. I'm guessing the square 64x64 pixel input was padded for input to the model, since it identifies a square in the middle and gives the coordinates for an upsampled image. These things can be fixed, but the description is still very basic and doesn't contain much actual information. 

I'll give it a D because it did the bare minimum.


![crop from MGCLS, containing multiple radio galaxies](https://github.com/elastufka/SAX-XRS_figures/blob/gh-pages/images/Florence2%20thoughts%20on%20the%20universe/mgcls_ep475img_box.png?raw=true)

_What Florence-2 thinks:_

*CAPTION*: a black and white image of a cluster of stars

*MORE_DETAILED_CAPTION*: The image is a black and white close-up of a textured surface. The surface appears to be made up of small, irregularly shaped particles that are scattered across the image. The particles are of varying sizes and shapes, with some being larger and some being smaller. The texture of the surface is rough and uneven, with small bumps and grooves visible. The image is taken from a top-down perspective, looking down on the surface.

*OD*: {'bboxes': [[0.12, 0.12, 255.87, 255.36]], 'labels': ['flower']}

_What I think:_

It's neither stars, (individual) particles, or a flower, and once again object detection just selects the whole image. Maybe a grounding phrase prompting selection of the brightest source could improve results? Otherwise, this one is a definite F.

## Solar Images (AIA)

![full disk image from AIA 305](https://github.com/elastufka/SAX-XRS_figures/blob/gh-pages/images/Florence2%20thoughts%20on%20the%20universe/f0304_crop_box.png?raw=true)

_What Florence-2 thinks:_

*CAPTION*: A bright red sun with a black background.

*MORE_DETAILED_CAPTION*: The image is a close-up of the sun as seen by NASA's Solar Dynamics Observatory. The sun appears to be a bright orange-red color with a rough, textured surface. It is surrounded by a black background, which makes the sun stand out even more. The surface of the planet is covered in small, jagged particles, giving it a fiery appearance. The overall color of the image is predominantly red and orange, with some areas appearing darker and more prominent.

*OD*: {'bboxes': [[71.31, 35.60, 3397.24, 3335.04]], 'labels': ['grapefruit']}

_What I think:_

Grapefruit. I love it. 

Maybe a full-disk image from SDO was the low-hanging fruit, because it's identified correctly. Minus points for the second-to-last sentence, which is all kinds of phrases that don't go together. Otherwise, it's a fairly generic description which I'll give a C.
