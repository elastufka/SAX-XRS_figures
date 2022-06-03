---
title: "Reprojecting STIX images"
image: 
  path: /images/transparent_banner.png
  thumbnail: /images/Reprojecting STIX images/hero.png
  caption:
categories:
  - posts
tags:
  - AIA
  - STIX
  - WCS
---

Previously, the reprojection of AIA maps to the Solar Orbiter reference frame has been shown. The method of reprojecting STIX images, reconstructed through one of many algorithms such as back projection, forward fit, CLEAN, or expectation maximization, is very similar. 

To obtain a STIX image map, visit the [STIX Data Center](https://datacenter.stix.i4ds.net/) and download a FITS file from the Image Preview archive (currently only available to registered users), along with the Python script that enables reading of the file as a SunPy map.

In this example, a simple back projection image shows a source near the limb to the bottom-right of the image.

![STIX back projection full-disk image](https://github.com/elastufka/SAX-XRS_figures/blob/gh-pages/images/Reprojecting%20STIX%20images/stix_fulldisk_8-26.png?raw=true)

From here on, the [SunPy reprojection tutorial](https://docs.sunpy.org/en/stable/generated/gallery/map_transformations/reprojection_different_observers.html#sphx-glr-generated-gallery-map-transformations-reprojection-different-observers-py) can be followed with the following exceptions:

* When constructing _out_header_:
```python 
out_header=sunpy.map.make_fitswcs_header((1,1),aia_map.reference_coordinate,wavelength=aia_map.wavelength)
```
  * use _out_shape_ = (1,1)
  * don't include the scale keyword argument
  * not necessary to change the solar radius
  * reference coordinate can be constructed from any _observer_ whose position details can be obtained from SPICE kernels

This header can then be [modified](https://elastufka.github.io/SAX-XRS_figures/posts/2022/01/18/A-faster-way-of-reprojecting-AIA-cutouts.html) to account for the correct shape and location of the reprojected submap if a submap is being used, and then used as input to _reproject_to()_.

The reprojected back projection image of a STIX flare on 26 August 2021 is shown below, then overlaid on the AIA 171Å image of the same area at 23:18:09. STIX contours are shown at 60%, 70%, 80%, 90% and 95%.

![reprojected STIX back projection image submap](https://github.com/elastufka/SAX-XRS_figures/blob/gh-pages/images/Reprojecting%20STIX%20images/stix_sm_rotated_8-26.png?raw=true)

![composite map of STIX contours on top of AIA 171 image](https://github.com/elastufka/SAX-XRS_figures/blob/gh-pages/images/Reprojecting%20STIX%20images/hero.png?raw=true)
