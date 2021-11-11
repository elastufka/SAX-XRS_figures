---
title: "Spacecraft Roll Angle and Apparent Solar Radius from Spiceypy"
image: 
  path: /images/transparent_banner.png
  thumbnail: /images/roll_hero.png
  caption:
categories:
  - posts
tags:
  - SPICE
  - STIX
  - WCS
---

The as-flown attitude of an orbiting spacecraft affects its local coordinate system. A roll angle correction must be applied to imaging data in order to recover the proper coordinates. Spacecraft attitude data, both predicted and as-flown, are stored in the [SPICE kernels](https://repos.cosmos.esa.int/socci/projects/SPICE_KERNELS/repos/solar-orbiter/browse).

Another factor that depends on the spacecraft location (especially for Solar Orbiter's highly elliptical orbit) is the apparent solar radius; the closer to the Sun, the larger the observed solar radius. To compare data from different dates, the apparent solar radius must be taken into account.  

Roll angle correction (not yet implemented in the STIX data pipeline) can be done via SSWIDL's <i>get_sunspice_roll.pro</i> function. The [Sunspice](https://hesperia.gsfc.nasa.gov/ssw/packages/sunspice/idl/) package is an IDL wrapper for the SPICE software, written in C. Similarly, the [Spicypy](https://spiceypy.readthedocs.io/en/main/) package is a wrapper written in Python.

I implemented a Python version of <i>get_sunspice_roll.pro</i> and added it to [ _stix_utils.py_](https://raw.githubusercontent.com/elastufka/solar_all_purpose/main/stix_utils.py). With Spicepy it is important to be aware that many functions (perhaps only those that use _spice_error_check_, although that is most of them) require that the working directory is the kernel directory or else the needed files risk not being found - annoying behaviour but hopefully something that can be eventually written out. Many thanks to M. Sitjà for assistance understanding the finer details of reference frames and ID codes.

For the STIX back-projection dataset of ~700 events spanning from January - September 2021, the difference between roll-angle (in degrees) calculated by Python and IDL was on average 8x10<sup>-6</sup> with a standard deviation of 2x10<sup>-4</sup> ; negligible.

Another addition to [ _stix_utils.py_](https://raw.githubusercontent.com/elastufka/solar_all_purpose/main/stix_utils.py) was _get_rsun_apparent()_, which gets the apparent solar radius given a datetime and an optional observer.

Illustrations of Solar Orbiter's as-flown roll angle and apparent solar radius for the last year are shown below.

{% include roll_angle.html %}




