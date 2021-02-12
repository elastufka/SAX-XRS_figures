---
title: "NuSTAR small flare of 12 September 2020"
categories:
  - posts
tags:
  - NuSTAR
  - XRT
  - AIA
  - STEREO
---

## Basic information

NuSTAR observation time (orbit 8): 2020-09-12 20:22:00 - 21:07:00


| Instrument | Wavelength regime | Cadence | Resolution/px |
| --- | --- | --- | --- |
| NuSTAR | SXR | 20s | low |
| XRT Be-Thin| SXR | 200s| 1"|
| AIA | EUV | 12 s | 0.6"|
| STEREO-A EUVI | EUV | 5 min | 1.6"|


## Flare Location

<figure>
<div class="row">
<div class="column">
<img src="https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/AIA335_boxes.png" alt="AIA 335 image with rectangle indicating where fluxes were calculated">  </div>
<div class="column">
<img src="https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/NuSTAR_A_boxes.png" alt="NuSTAR camera A low-energy image with rectangle indicating where fluxes were calculated">
<figcaption>Rectangles describing regions where lightcurve fluxes were calculated. The 40" square box shown above was used for XRT, AIA, and STEREO-A (not shown). The 160" square box shown below was used for NuSTAR. Coordinates of box centers are given below.</figcaption>  </div>
</div>
</figure>

Flare location determined by first aligning XRT to AIA (~10" offset from location in XRT header) then finding the position of the center of mass of the 90% contour of the XRT submap around the flare area.

```python
[<SkyCoord (Helioprojective: obstime=2020-09-12 20:27:01, rsun=695508000.0 m, observer=<HeliographicStonyhurst Coordinate (obstime=2020-09-12 20:27:01): (lon, lat, radius) in (deg, deg, m)
( 0.,  7.22972093,   1.50532432e+11)>): (Tx, Ty) in arcsec
(-883.70237088,  221.77460855)>]
```

## Flare time evolution (AIA and STEREO)

3-minute integrated AIA 94 images

|  Source | Image | Base Difference | Sobel Filter | 
| --- | --- | --- | --- |
| AIA 94 | <figure><img src="https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/AIA94_b2_nofilter.gif" alt="AIA 94 gif" width="150"></figure>| <figure><img src="https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/AIA94_b2_diff.gif" alt="AIA 94 difference gif" width="150"></figure> |<figure><img src="https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/AIA94_b2_sobel.gif" alt="AIA 94 Sobel gif" width="150"></figure> |
| STEREO-A 195 | <figure><img src="https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/STEREO_orbit8_b1_nofilter_b2.gif" alt="STEREO 195 gif" width="150"></figure> |<figure><img src="https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/STEREO_orbit8_b2_diff_big.gif" alt="STEREO 195 difference gif" width="150"></figure>  | <figure><img src="https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/STEREO_orbit8_b2_sobel.gif" alt="STEREO 195 Sobel gif" width="150"></figure> |

<!--
![STEREO 195 difference gif](https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/STEREO_orbit8_b2_diff_big.gif) 
-->

## Lightcurves

AIA at native cadence except for AIA 193 (3 minutes currently, will be updated later)

STEREO at native cadence (5 minutes).

NuSTAR images at 20s cadence (made by Sam), adjusted to counts. 

{%include temp-plot.html %} 
