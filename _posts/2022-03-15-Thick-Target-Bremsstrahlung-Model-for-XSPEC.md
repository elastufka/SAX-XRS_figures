---
title: "Thick Target Bremsstrahlung Model for XSPEC"
image: 
  path: /images/transparent_banner.png
  thumbnail: /images/Thick Target Bremsstrahlung Model for XSPEC/hero.png
  caption:
categories:
  - posts
tags:
  - STIX
  - xspec
  - examples
---

NASA's [X-ray Spectral Fitting Package](https://heasarc.gsfc.nasa.gov/xanadu/xspec/) lacks one of the key solar flare emission models, that of thick-target bremsstrahlung. In _sswidl's_ OSPEX, this model is implemented as _thick2.pro_. Using [sunxspex's](https://github.com/sunpy/sunxspex)
_emission_ module, the thick-target model can be adapted for use with XSPEC or PyXspec. 

The current implementation of the model has not been optimized to take advantage of numpy, but is rather a direct translation from IDL. XSPEC-compatible models based on sunxspex can be found [here](https://github.com/elastufka/sunxspex/blob/master/sunxspex/sun_xspec.py). 

## Example 

Full example code can be found [here](https://github.com/elastufka/sunxspex/blob/master/examples/pyxspec_example.py). A single STIX spectrum is fit with a thermal bremsstrahlung model (XSPEC's _apec_) plus a thick-target model, in multiple stages. The reduced output is reproduced below.

{%include xspec_output.md %}

##  Results

{%include thicktarget.html %}

## Remarks

- No background has been specified in this example.
- Fitting is still slow, on the order of 10s, which is comparable to OSPEX. Should this remain the case, the only major advantages of XSPEC over OSPEX (mulitple instruments, fit methods, error calculation MCMC) are likely to be important only for special cases. 
- If the break energy _eebrk_ is at any point less than the lower energy limit _eelow_, the original sunxspex code raises an exception. This behaviour will cause XSPEC to fail, so when this occurs the model instead makes no change to the calculated flux vector. This can cause long loops with no improvement, if XSPEC continues to vary the parameters in the space where _eebrk_ < _eelow_. In the example, _setPars()_ is used to ensure that _eebrk_ is always greater than _eelow_. A better solution will need to be found for the future.
- This model has not yet been tested for the fitting of multiple spectra.
- This model does not make use of numpy's module for dealing with Legendre series.
- Unlike _sunxspex_ models, this model takes in unitless arrays. However, units are controlled by XSPEC - counts/s are converted to photons/s.
- Currently the correct behaviour of this model is partially dependent on an external file containing the coronal abundances, which are not native to XSPEC. In the future this should be changed to take advantage of _sunxspex's_ abundance calculations.




