---
title: "NuSTAR small flare of 12 September 2020 - orbit 6"
categories:
  - posts
tags:
  - NuSTAR
  - XRT
  - AIA
  - STEREO
---

## Basic information

NuSTAR observation time (orbit 6): 2020-09-12 17:13:00 - 17:40:00


| Instrument | Wavelength regime | Cadence | Resolution/px |
| --- | --- | --- | --- |
| NuSTAR | SXR | 20s | low |
| XRT Be-Thin| SXR | 200s| 1"|
| AIA | EUV | 12 s | 0.6"|
| STEREO-A EUVI | EUV | 5 min | 1.6"|


## Flare Location

<figure>
<img src="https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/orbit6/orbit6_overview.png" alt="XRT, NuSTAR camera A low-evergy and AIA 335 image with rectangles indicating where fluxes were calculated">  
</figure>

Flare location determined by finding the position of the center of mass of the 90% contour of the XRT submap around the flare area. To align with AIA, this requires ~25" offset in x and ~20" in y from the location in XRT header (coordinates below given in XRT frame).

```python
[<SkyCoord (Helioprojective: obstime=2020-09-12 17:15:54, rsun=695508000.0 m, observer=<HeliographicStonyhurst Coordinate (obstime=2020-09-12 17:15:54): (lon, lat, radius) in (deg, deg, m)
( 0.,  7.23099555,   1.50537582e+11)>): (Tx, Ty) in arcsec
(-605.34259198,  41.25279285)>]
```

## Flare time evolution (AIA and STEREO)

3-minute integrated AIA 193 images

|  Source | Image | Base Difference | Sobel Filter | 
| --- | --- | --- | --- |
| AIA 193 | <figure><img src="https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/orbit6/AIA193_nofilter.gif" alt="AIA 193 gif" width="150"></figure>| <figure><img src="https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/orbit6/AIA193_diff.gif" alt="AIA 193 difference gif" width="150"></figure> |<figure><img src="https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/orbit6/AIA193_sobel.gif" alt="AIA 193 Sobel gif" width="150"></figure> |
| STEREO-A 195 | <figure><img src="https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/orbit6/STEREO195_nofilter.gif" alt="STEREO 195 gif" width="150"></figure> |  | <figure><img src="https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/orbit6/STEREO195_sobel.gif" alt="STEREO 195 Sobel gif" width="150"></figure> |


## Lightcurves

AIA and XRT at native cadence, calculated using 40" box. 

STEREO-A at native cadence (5 minutes), calculated using 40" box. 

NuSTAR images at 20s cadence (made by Sam), adjusted to counts, calculated using 160" square box. 

{%include orbit6_lightcurves.html %}\

<!--
## Masks

Find regions of brightening/dimming by comparing the change in the flare region vs the quiet Sun region. A pixel is included in 'brightening' mask if the value of that pixel in the _difference_ image (integrate flare X-ray peak minus integrated pre-flare) is >3x greater than standard deviation of the average flux difference in Quiet Sun ($$\sigma_{QSdiff}$$) in those same time ranges (details in code below). Likewise with 'dimming' mask, only the pixel value is less than -3x {% raw %}$$\sigma_{QSdiff}$${% endraw %}. The total mask is sum of both masks in each channel.

```python
#pre-flare time range (according to XRT, NuSTAR) 20:22-20:32
#select time ranges to integrate images
pfs=dt.strptime('20200912_202200','%Y%m%d_%H%M%S')
pfe=dt.strptime('20200912_203200','%Y%m%d_%H%M%S')
#peak time range (according to XRT, NuSTAR) 20:39-20:49
#integrate whole image. de-rotation doesn't shift more than ~1px, safe enough to do difference images like this
kfs=dt.strptime('20200912_203900','%Y%m%d_%H%M%S')
kfe=dt.strptime('20200912_204900','%Y%m%d_%H%M%S')

mask_total=np.ma.masked_inside(m.data,-3*t,3*t)
mask_plus.append(np.ma.masked_less(m.data,3.*t).mask) #1 means masked, 0 means un-masked, this is why it masked_less and masked_greater are used where they are
mask_minus.append(np.ma.masked_greater(m.data,-3.*t).mask) 
```

![Masks for all AIA channels](https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/AIA_masks.png) 


## Lightcurves with masks

{%include dim-bright-total.html %}\

## DEM
-->
