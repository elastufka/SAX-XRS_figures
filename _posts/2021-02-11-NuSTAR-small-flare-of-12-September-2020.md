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


| Instrument | Wavelength regime | Cadence | Resolution |
| --- | --- | --- | --- |
| NuSTAR | SXR | 20s | low |
| XRT Be-Thin| SXR | 30s?| medium|
| AIA | EUV | 18-ish s | 0.7"|
| STEREO-A EUVI | EUV | 5 min | 1.something"|


Location determined by aligning XRT to AIA

## Figure 1: Flare Location

<figure class="half">
<img src="https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/AIA335_boxes.png" alt="AIA 335 image with rectangle indicating where fluxes were calculated">
<img src="https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/NuSTAR_A_boxes.png" alt="NuSTAR camera A low-energy image with rectangle indicating where fluxes were calculated">
<figcaption>Rectangles describing regions where lightcurve fluxes were calculated. The 40" square box shown on the left was used for XRT, AIA, and STEREO-A (not shown). The 160" square box shown on the left was used for NuSTAR. Coordinates of box centers are given below.</figcaption>
</figure>

```python
[<SkyCoord (Helioprojective: obstime=2020-09-12 20:27:01, rsun=695508000.0 m, observer=<HeliographicStonyhurst Coordinate (obstime=2020-09-12 20:27:01): (lon, lat, radius) in (deg, deg, m)
( 0.,  7.22972093,   1.50532432e+11)>): (Tx, Ty) in arcsec
(-883.70237088,  221.77460855)>]
```

## Figure 2: Flare time evolution (AIA and STEREO)

|  Source | Image | Base Difference | Sobel Filter | 
| --- | --- | --- | --- |
| AIA 94 | ![AIA 94 gif](images/AIA_094_orbit8_3min.gif) | ![AIA 94 difference gif](images/AIA_094_orbit8_3min.gif)  | ![AIA 94 Sobel gif](images/AIA_094_orbit8_3min.gif)  |
| STEREO-A 195 | <figure><img src="https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/STEREO_orbit8_b1_nofilter_b2.gif" alt="STEREO 195 gif" width="150"></figure> |<figure><img src="https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/STEREO_orbit8_b2_diff_big.gif" alt="STEREO 195 difference gif" width="150"></figure>  | <figure><img src="https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/STEREO_orbit8_b2_sobel.gif" alt="STEREO 195 Sobel gif" width="150"></figure> |

<!--
![STEREO 195 difference gif](https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/STEREO_orbit8_b2_diff_big.gif) 
-->

## Figure 2: Lightcurves

AIA at native cadence except for AIA 193 (3 minutes currently, will be updated later)

STEREO at native cadence (5 minutes).

(show boxes used for lightcurves? new figure)

{%include temp-plot.html %} 
