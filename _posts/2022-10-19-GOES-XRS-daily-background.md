---
title: "GOES XRS daily background"
image: 
  path: /images/transparent_banner.png
  thumbnail: /images/GOES XRS daily background/hero.png
  caption:
categories:
  - posts
tags:
  - GOES
  - STIX
  - spectroscopy
---

## Daily background

Daily X-ray background measurements are available for the last seven days at the Space Weather Prediction Center [SWPC](https://services.swpc.noaa.gov/json/goes/primary/xray-flares-7-day.json). The full dataset can be found [here](https://data.ngdc.noaa.gov/platforms/solar-space-observing-satellites/goes/goes16/l2/data/xrsf-l2-bkd1d_science/). No scaling factor is necessary for this data, as it is in physical units. To determine the daily background, 
 hourly and 8-hour minima of the 1-minute averages are used. The 1-8 $$\AA$$ (long) and 0.5-4 $$\AA$$ (short) background fluxes are shown below, from February 2017 until October 2022. The daily average flux can also be toggled on.

{%include xrs_bkg.html %}

## Flare-dectection defined background

The [XRS summary files](https://data.ngdc.noaa.gov/platforms/solar-space-observing-satellites/goes/goes16/l2/data/xrsf-l2-flsum_science/) also include background measurements, which are defined based on the [flare-finding algorithm]().

The slight differences between the backgrounds, as well as what they mean for flare classes when background-subtracted, are illustrated in the figure below, for solar flares detected by GOES from 

{%include xrs_flares.html %}

## GOES and STIX backgrounds

STIX daily backgrounds are also available from the [STIX data center](https://datacenter.stix.i4ds.net/). They are displayed here in the ranges that have partial overlap with the GOES short- and long-wavelength channels. 

{%include XRS_STIX_bkg.html %}

The comparison between XRS and STIX cannot be direct. For one, the position of Solar Orbiter varies rapidly with respect to the Earth in both distance and angle, neither of which is evident in this plot. What this figure does illustrate is the generally low background of STIX, the dominance of the onboard source, and the sensitivity of the instrument in periods of high solar activity. 

## GOES and STIX response functions 

The different range of sensitivity of XRS and STIX is best illustrated by the instrument response functions. 

{%include GOES_STIX_response.html %}


