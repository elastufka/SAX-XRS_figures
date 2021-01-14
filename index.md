---
title: "GOES-class Estimation for Behind-the-limb Solar Flares Using MESSENGER SAX"
sub_title: "E. Lastufka (FHNW/ETHZ) and S. Krucker (FHNW/UC Berkeley)"
categories:
  - Markup
elements:
  - content
  - css
  - formatting
  - html
  - markup
last_modified_at: 2018-02-01T10:16:49-05:00
---

_E. Lastufka (FHNW/ETHZ) and S. Krucker (FHNW/UC Berkeley)_

Published in [ApJ](https://doi.org/10.3847/1538-4357/abc5c2), or read the pre-publicatation article on [arxiv.org](https://arxiv.org/abs/2012.10221) 

## Abstract

Mercury mission MESSENGER's Solar Assembly for X-rays (SAX) observed almost 700 solar flares between May 28, 2007 and August 19, 2013, as cataloged by [Dennis 2015](http://adsabs.harvard.edu/abs/2015ApJ...803...67D). The SAX instrument, part of the X-ray Spectrometer (XRS), operated at 1 - 10 keV, partially overlapping the energy range of the GOES X-ray spectrometers. SAX provides viewing angles different from the Earth-Sun line and can therefore be used as a GOES proxy for partially or fully occulted flares as seen from Earth. For flares with GOES classes above C2 seen on-disk for both instruments, we found an empirical relationship between the soft X-ray (SXR) fluxes measured by both SAX and GOES. Due to the different energy response of the two SXR instruments, individual events can deviate on average by about a factor of two from the empirical relationship, implying that predictions of the GOES class of occulted flares from SAX data are therefore accurate to within the same factor.

The distinctive GOES energy response in combination with the multithermal nature of flares makes it difficult for any instrument, even other soft X-ray spectrometers, to provide a GOES proxy more accurate than a factor of two.

## Figure 1

The soft X-ray instrument normalized response functions (above) and the MESSENGER data set of ~650 flares (below), represented by the spectra at the flare peak. The flare of 1 June, 2007, which is shown in additional detail in Figure 1 of [Dennis 2015](http://adsabs.harvard.edu/abs/2015ApJ...803...67D), is highlighted in red. The range from 2.5-7.5 keV is used in Section 2.2 to fit the MESSENGER spectra.

{% include SXR_instr_response.html %}
{% include all_Mess_spectra.html %}


## Figure 2

Locations of flares as given by HEK/AIA. Flares are color-coded according to the ratio of the theoretical GOES flux calculated from the MESSENGER temperature and emission measure to the actual GOES flux (see Figure 4 - MESSENGER/GOES < 1 is cyan and >1 is magenta) and the size of the symbol associated with them is directly proportional to the value of the ratio. Events marked with a plus sign indicate those where the measured GOES flux is less than class C2, corresponding to the red triangles in [Figure 4](#figure-4).

{% include all_flare_locations.html %}


## Figure 3

Relationship of MESSENGER peak flux to GOES peak flux, for events visible to both satellites. The lines of best fit above a lower threshold (C2 for GOES long, B2 for GOES short) are also shown.

{% include direct.html %}


## Figure 4

Events which were excluded from the samples above in [Figure 3](#figure-3). Although jointly visible to MESSENGER and GOES, events marked in red were deemed unsuitable for other reasons, described in the text.

{% include outliers.html %}


## Figure 5

Relationship of GOES-equivalent flux derived from the MESSENGER spectra to the measured GOES flux, for all jointly observed flares above a certain flux threshold (C2 for GOES long, B2 for GOES short). The solid line shows line of best fit, while the dashed line is the 1:1 ratio.

{% include goes_teem.html %}


## Figure 6

Temperatures and emission measures calculated for each instrument. MESSENGER values were obtained via OSPEX fit, while GOES quantities were calculated using the SSWIDL routine _goes_teem.pro_, based on empirical data.

{% include TEM.html %}


## Figure 7

Comparison of SXR fluxes with EUV flux. Lines of best fit are shown in blue. In the top plot, the dashed line indicates the fit found in [Nitta et al. 2013](http://link.springer.com/article/10.1007/s11207-013-0307-7) and begins at the value above which the fit is best (GOES M5.5 or 4x10<sup>6</sup> photons/s in EUV 195 Å). In the middle plot, it illustrates the derived MESSENGER proxy (Equation 1), after conversion via the EUV-GOES proxy (Equation 5). In the bottom plot, the dashed line indicates the 1:1 ratio.

{% include STEREO.html %}


