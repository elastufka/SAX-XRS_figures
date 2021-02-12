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

## Figure 2: Flare time evolution (AIA and STEREO)

|  Source | Image | Base Difference | Sobel Filter | 
| --- | --- | --- | --- |
| AIA 94 | ![AIA 94 gif](images/AIA_094_orbit8_3min.gif) | ![AIA 94 difference gif](images/AIA_094_orbit8_3min.gif)  | ![AIA 94 Sobel gif](images/AIA_094_orbit8_3min.gif)  |
| STEREO-A 195 | ![STEREO 195 gif](/mages/STEREO_orbit8_b1_nofilter_b2.gif) | ![STEREO 195 difference gif](/images/STEREO_orbit8_b2_diff_big.gif)  | <figure><img src="../images/STEREO_orbit8_b2_sobel.gif" alt="STEREO 195 Sobel gif"></figure> |

<figure>
<img src="../images/STEREO_orbit8_b2_sobel.gif" alt="STEREO 195 Sobel gif">
</figure>

![STEREO 195 difference gif](../images/STEREO_orbit8_b2_diff_big.gif) 

![test png](../images/misolfa_transm.png) 

<figure>
<img src="../images/misolfa_transm.png" alt="another test">
</figure>

<figure>
<img src="https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/misolfa_transm.png" alt="yet another test">
</figure>

## Figure 2: Lightcurves

AIA at native cadence except for AIA 193 (3 minutes currently, will be updated later)

STEREO at native cadence (5 minutes).

(show boxes used for lightcurves? new figure)

{%include temp-plot.html %} 
