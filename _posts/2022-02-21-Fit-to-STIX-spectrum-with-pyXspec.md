---
title: "Fit to STIX spectrum with pyXspec"
image: 
  path: /images/transparent_banner.png
  thumbnail: /images/Fit to STIX spectrum with pyXspec/hero.png
  caption:
categories:
  - posts
tags:
  - STIX
  - xspec
  - examples
---

STIX spectrogram FITS files are not natively compatible with NASA's [X-ray Spectral Fitting Package](https://heasarc.gsfc.nasa.gov/xanadu/xspec/). However, work is ongoing such that this powerful, free software can be used with STIX spectra, should _sswidl's_ OSPEX prove insufficient (ex., OSPEX can only fit with chi-squared minimization and one spectrum at a time).

This example demonstrates the results of fitting a broken power law with coronal abundances to a STIX spectrum. 
    
## Input

Input files are named identically to those accepted by OSPEX: a FITS file containing the spectrogram, with multiple rows and the file name extension _.fits_, and a temperature response matrix with the file name extension _.srm_, that is referred to in the spectrogram FITS header.  

The spectrogram and response function are shown below.

{%include stix_sgram.html %}

{%include trmatrix.html %}

Zooming in and looking at the index shows that for the flare peak from 17:24:30 - 17:25:30, the correct row has index 13 (indices in XSPEC are from 1 not 0).  

Data is then loaded into XSPEC with the row specifier in curly braces, for example:

    xspec.AllData("1:1 stx_spectrum_20210908_1712.fits{13}")
    
The spectrum of the single time bin is shown below.

<img src="https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/single-spec.png" alt="STIX Count spectrum for single time bin at flare peak"> 

### Specifying Coronal Abundances

XSPEC does not natively support solar coronal abundances, only photoshperic. Like in the [NuSTAR example](https://elastufka.github.io/SAX-XRS_figures/posts/2021/08/23/Fit-to-NuSTAR-spectrum-with-pyXspec-example.html), specify the abundance file manually.

    xspec.Xset.abund="file %s" % abundf
    
## Model Set-up

The chosen model is a [broken power law](https://heasarc.gsfc.nasa.gov/xanadu/xspec/manual/node141.html). By default the break energy is 5 keV, which is low for solar flares, so initially it can be set higher. Here it is set with an initial value of 15 keV, increments in 0.1 keV and a maximum of 18 keV. This parameter will automatically be frozen.

    m1=xspec.Model("bknpower")
    m1.setPars({2:"15.0 -.1,,,18"})
    
Fitting once over an energy range of 8-30 keV results in a chi-squared statistic of ~ 2000. This can be improved by a second fit, now letting the break energy parameter vary freely, by unfreezing it before fitting again:
    
    p2=getattr(m1.bknpower,'BreakE') 
    p2.frozen=False
    
The chi-squared statistic of the fit is now a much more reasonable 40. Note that initially fitting with the default break energy parameters will result in a very low break energy and a higher chi-squared, instead of reaching the better solution provided by fitting twice. 

##  Results

{%include specfit.html %}




