---
title: "NuSTAR small flare of 12 September 2020 - orbit 4"
image: 
  path: /images/transparent_banner.png
  thumbnail: /images/orbit4/orbit4_overview.png
  caption:
categories:
  - posts
tags:
  - NuSTAR
  - XRT
  - AIA
  - STEREO
---

## Basic information

NuSTAR observation time (orbit 4): 2020-09-12 14:00:00 - 14:23:00


| Instrument | Wavelength regime | Cadence | Resolution/px |
| --- | --- | --- | --- |
| NuSTAR | SXR | 20s | low |
| XRT Be-Thin| SXR | 200s| 1"|
| AIA | EUV | 12 s | 0.6"|
| STEREO-A EUVI | EUV | 5 min | 1.6"|


## Flare Location

<figure>
<img src="https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/orbit4/orbit4_overview.png" alt="XRT, NuSTAR camera A low-evergy and AIA 335 image with rectangles indicating where fluxes were calculated">  
</figure>

Flare location determined by finding the position of the center of mass of the 90% contour of the XRT submap around the flare area. To align with AIA, this requires ~25" offset in x and ~25" in y from the location in XRT header (coordinates below given in XRT frame).

```python
<SkyCoord (Helioprojective: obstime=2020-09-12 14:10:41, rsun=695508000.0 m, observer=<HeliographicStonyhurst Coordinate (obstime=2020-09-12 14:10:41): (lon, lat, radius) in (deg, deg, m)
( 0.,  7.23219551,   1.50542567e+11)>): (Tx, Ty) in arcsec
(-764.11429488,  1.2117822)>
```

## Flare time evolution (AIA and STEREO)

3-minute integrated AIA 193 images

|  Source | Image | Base Difference | Sobel Filter | 
| --- | --- | --- | --- |
| AIA 193 | <figure><img src="https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/orbit4/AIA193_nofilter.gif" alt="AIA 193 gif" width="150"></figure>| <figure><img src="https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/orbit4/AIA193_diff.gif" alt="AIA 193 difference gif" width="150"></figure> |<figure><img src="https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/orbit4/AIA193_sobel.gif" alt="AIA 193 Sobel gif" width="150"></figure> |

<!--
| STEREO-A 195 | <figure><img src="https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/orbit6/STEREO195_nofilter.gif" alt="STEREO 195 gif" width="150"></figure> |  | <figure><img src="https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/orbit6/STEREO195_sobel.gif" alt="STEREO 195 Sobel gif" width="150"></figure> |
-->


## Lightcurves

AIA and XRT at native cadence, calculated using 40" box. 

STEREO-A at native cadence (5 minutes), calculated using 40" box. 

NuSTAR images at 20s cadence (made by Sam), adjusted to counts, calculated using 160" square box. 

{%include orbit4_lightcurves.html %}


## Masks

Find regions of brightening/dimming by comparing the change in the flare region vs the quiet Sun region. A pixel is included in 'brightening' mask if the value of that pixel in the _difference_ image (integrate flare X-ray peak minus integrated pre-flare) is >3x greater than standard deviation of the average flux difference in Quiet Sun ((𝜎_<sub>QSdiff</sub>) in those same time ranges (details in code below). Likewise with 'dimming' mask, only the pixel value is less than -3x  𝜎_<sub>QSdiff</sub>. The total mask is sum of both masks in each channel.


![Masks for all AIA channels](https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/orbit4/orbit4_masks.png) 


## Lightcurves with masks

{%include orbit4_dim_bright_total.html %}

<!--

## DEM
-->
