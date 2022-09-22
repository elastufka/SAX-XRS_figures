---
title: "Cropping and Combining STIX spectrograms"
image: 
  path: /images/transparent_banner.png
  thumbnail: /images/Cropping and Combining STIX spectrograms/hero.png
  caption:
categories:
  - posts
tags:
  - STIX
  - spectroscopy
---

To select an event of interest from a long-duration spectrogram or pixel data file, one may want to reduce the file to a smaller size containing only that time period. Similarly, one might want to combine observations to cover a longer time period.

A demonstration of how to do this is available on [Colab](https://colab.research.google.com/drive/1bHgPoQGG_5dq6PZuuaN9kPoJa_3ifLh6?usp=sharing), along with links to the applicable code.

![STIX spectrogram](https://github.com/elastufka/SAX-XRS_figures/blob/gh-pages/images/Cropping%20and%20Combining%20STIX%20spectrograms/spec1.png?raw=true)
Figure 1: A STIX spectrogram

![STIX spectrogram for the following time period](https://github.com/elastufka/SAX-XRS_figures/blob/gh-pages/images/Cropping%20and%20Combining%20STIX%20spectrograms/spec2.png?raw=true)
Figure 2: STIX spectrogram for the following time period

![Lightcurve of STIX observations combined to cover the longer time period](https://github.com/elastufka/SAX-XRS_figures/blob/gh-pages/images/Cropping%20and%20Combining%20STIX%20spectrograms/spec_combine.png?raw=true)
Figure 3: Lightcurve of STIX observations combined to cover the longer time period

![STIX spectrogram cropped to select small solar flare](https://github.com/elastufka/SAX-XRS_figures/blob/gh-pages/images/Cropping%20and%20Combining%20STIX%20spectrograms/spec_crop.png?raw=true)
Figure 4: STIX spectrogram cropped to select small solar flare

Things to note: 

1) Time is relative measured from the start time of the observation, so new start times resulting from cropping or combining have to be accounted for.

2) When concatenating two spectrograms, a warning is issued if there is a gap in time between the two files that is longer than the duration of the last time bin in the first file. When there is an overlap in times between the two observations, the data from the first (in time) spectrogram is kept. Metadata (request ID, etc) from the first file is kept.

3) If the energy bin masks, pixel masks, or detector masks - which indicate which of these quantities is in use in the observation - in the two observations do not match, the concatenation will fail.

4) No light travel time correction, livetime correction, or background subtraction is applied. The processing level of the output remains the processing level of the input. 


