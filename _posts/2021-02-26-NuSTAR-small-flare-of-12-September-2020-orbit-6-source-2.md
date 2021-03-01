---
title: "NuSTAR small flare of 12 September 2020 - orbit 6 source 2"
categories:
  - posts
tags:
  - NuSTAR
  - XRT
  - AIA
  - STEREO
---

A second, much fainter source also close to the edge of the NuSTAR FOV examined with the initial intent of determining if the brighter source in the orbit left the FOV during the observation, thus accounting for the sudden drop in counts around 17:19. 

As will be seen, this was inconclusive due to the general low number of counts in the area of source 2, but given the total counts did not drop to zero, it's likely that any shift in NuSTAR's pointing during the observation was not enough to exclude either source from its FOV. 

The event has enough counts to be interesting on its own, and the XRT Be-Thin observation fortuituously coincides with the peak of the NuSTAR counts. 

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
<img src="https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/orbit6/orbit6_overview_s2.png" alt="XRT, NuSTAR camera A low-evergy and AIA 335 image with rectangles indicating where fluxes were calculated">  
</figure>

Flare location determined by finding the position of the center of mass of the 90% contour of the XRT submap around the flare area. To align with AIA, this requires ~25" offset in x and ~20" in y from the location in XRT header (coordinates below given in XRT frame).

```python
<SkyCoord (Helioprojective: obstime=2020-09-12 17:12:34, rsun=695508000.0 m, observer=<HeliographicStonyhurst Coordinate (obstime=2020-09-12 17:12:34): (lon, lat, radius) in (deg, deg, m)
( 0.,  7.23101745,   1.50537672e+11)>): (Tx, Ty) in arcsec
(-809.33945694,  330.72860268)>
```

## Flare time evolution (AIA and STEREO)

3-minute integrated AIA 193 images

|  Source | Image | Base Difference | Sobel Filter | 
| --- | --- | --- | --- |
| AIA 193 | <figure><img src="https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/orbit6/AIA193_nofilter_s2.gif" alt="AIA 193 gif" width="150"></figure>| <figure><img src="https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/orbit6/AIA193_diff_s2.gif" alt="AIA 193 difference gif" width="150"></figure> |<figure><img src="https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/orbit6/AIA193_sobel_s2.gif" alt="AIA 193 Sobel gif" width="150"></figure> |
| STEREO-A 195 | <figure><img src="https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/orbit6/STEREO_195_nofilter_s2.gif" alt="STEREO 195 gif" width="150"></figure> |  | <figure><img src="https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/orbit6/STEREO_195_sobel_s2.gif" alt="STEREO 195 Sobel gif" width="150"></figure> |


## Lightcurves

AIA and XRT at native cadence, calculated using 40" box. 

STEREO-A at native cadence (5 minutes), calculated using 40" box. Because the source is close to the AIA limb, the longitude in STEREO-A was difficult to determine and this seems like the most likely source. Offset from XRT centroid coordinates: xoff=55, yoff=35 

NuSTAR images at 20s cadence (made by Sam), adjusted to counts, calculated using 160" square box. 

{%include orbit6_lightcurves_s2.html %}\


## Masks

Find regions of brightening/dimming by comparing the change in the flare region vs the quiet Sun region. A pixel is included in 'brightening' mask if the value of that pixel in the _difference_ image (integrated flare X-ray peak minus integrated pre-flare) is >5x greater than standard deviation of the average flux difference in Quiet Sun ($$\sigma_{QSdiff}$$) in those same time ranges (details in code below). Likewise with 'dimming' mask, only the pixel value is less than -5x {% raw %}$$\sigma_{QSdiff}$${% endraw %}. The total mask is sum of both masks in each channel.

Rows in figure show, for each wavelength:
- flare region integrated difference image
- quiet Sun integrated difference region image
- brightening mask
- dimming mask
- total mask

```python
#orbit6 s2
preflare_tr=['20200912_171000','20200912_171500']
flare_tr=['20200912_172400','20200912_172900']
flare_box=([-825,325],[-750,400])
qs_box=([-900,400],[-750,500])
```

![Masks for all AIA channels](https://github.com/elastufka/SAX-XRS_figures/raw/gh-pages/images/orbit6/orbit6_AIA_masks_s2.png) 


## Lightcurves with masks

{%include orbit6_s2_dim_bright_total.html %}\

<!--
## DEM

-->
