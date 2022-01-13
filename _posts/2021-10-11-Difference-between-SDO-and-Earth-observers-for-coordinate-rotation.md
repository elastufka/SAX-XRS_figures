---
title: "Difference between SDO and Earth observers for coordinate rotation"
image: 
  path: /images/transparent_banner.png
  thumbnail: /images/Difference between SDO and Earth observers for coordinate rotation/hero.png
  caption:
categories:
  - posts
tags:
  - AIA
  - STIX
  - WCS
---

The SPICE kernels used to get spacecraft or other oribiting body positions does not contain information for the SDO; therefore it is common to assume an Earth observer when considering coordinates associated with SDO/AIA data. Exact SDO location information is available through the FITS file headers. It's inconvenient to download a large, fulldisk SDO image just to get its header, which is the way almost everyone knows how to access these keywords. There are lesser-known and/or used ways of getting header information alone, through [dmrs](https://docs.sunpy.org/projects/drms/en/v0.5.5/) or [JSOC records queries](http://jsoc.stanford.edu/ajax/lookdata.html?ds=aia.lev1_euv_12s). 

The Earth-observer assumption is fairly accurate for coordinates on the solar disk, to ~30" radially from the solar limb. I illustrate this here by doing the following:

- Getting the AIA location for solar flares from the HEK database (chosen flares correspond to events at the same time as STIX flares)
- Assuming an Earth-observer for the coordinates
- Alternatively, getting the exact SDO location from the FITS headers and applying that observer to the coordinates
- Rotating each coordinate to the Solar Orbiter point-of-view (if possible)
- Comparing the difference between rotated coordinates
    
The figure shows that for AIA flares occuring near the solar limb, the reference frame of the observer (Earth or SDO) can make a difference of up to 15" in HPC x-coordinate or radially.

{%include STIX_flare_coord_diff.html %}

This can be shown more uniformly by sampling coordinates at a set radial distance and various angles. I show this for the solar limb, where the difference in HPC-x coordinate can be up to 8.5" and the difference in HPC-y up to 1". Note that the limb here is about 20" less than the approximate solar limb at 956", due to the fact that some coordinate pairs don't return a result upon rotation at a greater radial distance than this. 

{%include xy3D.html %}

The differences in x- and y- have a sinusoidal dependence on angle, when the cartesian coordinates shown above are converted to polar. Fitting a sine curve to these differences can be done with very little error, resulting in the fit paramaters shown below. The dependence of these fit parameters is shown according to radial distance from Sun center, with frequency and phase being almost constant for all cases.  

{%include SDO_Earth_fitparams.html %}


