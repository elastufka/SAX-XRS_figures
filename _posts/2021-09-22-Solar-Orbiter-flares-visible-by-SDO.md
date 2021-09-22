---
title: "Solar Orbiter flares visible by SDO"
image: 
  path: /images/transparent_banner.png
  thumbnail: /images/flareloc_hero.jpg
  caption:
categories:
  - posts
tags:
  - AIA
  - STIX
  - WCS
---

Solar Orbiter's STIX has observed over 1000 flare candidates as of September 2021. Of those, 358 are given locations by the Coarse Flare Locator. Joint visibility with Earth-orbiting SDO can be determined using ephemeris information from Solar Orbiter, contained in the Spice kernels, and the Earth. Code is [here](https://github.com/elastufka/STIX-science/blob/main/Python/visible_from_earth.py).

The 24 jointly visible flares are plotted below, with additional information available through the hovertext. 

{%include joint_observed.html %}
