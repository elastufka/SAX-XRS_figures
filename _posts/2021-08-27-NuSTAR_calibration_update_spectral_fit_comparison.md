---
title: "NuSTAR calibration update spectral fit comparison"
image: 
  path: /images/transparent_banner.png
  thumbnail: /images/nustar_cal_hero.png
  caption:
categories:
  - posts
tags:
  - NuSTAR
  - xspec
  - DEM
---

## Spectral fit

A patch to CALDB (currently in testing phase, not yet released) allows reliable fitting to lower energy ranges. New count, response, and background files for the [X-ray peak of the 20 September 2020 flare](https://elastufka.github.io/SAX-XRS_figures/posts/2021/02/11/NuSTAR-small-flare-of-12-September-2020-orbit-8.html) were generated using the patch. Fits were run with [pyXspec](https://elastufka.github.io/SAX-XRS_figures/posts/2021/08/23/Fit-to-NuSTAR-spectrum-with-pyXspec-example.html ) in two energy ranges: the original 2.5-4.5 keV and an expanded 2.2-4.5 keV range. 

Fitting with the original energy range produced identical results. None of the count values in the low energy (<2.2 keV) range were actually changed by the new calibration in this particular case.

| Energy range (keV) | T (MK)| EM (cm<sup>-3</sup>) |
|---|---|---|
| 2.5 - 4.5 | 2.91 (2.58 - 3.3) | 7.32e+43 (0 - 2.79e+44) |
| 2.2 - 4.5 | 3.31 (3.07 - 3.55) | 2.14e+43 (1.3e+43 - 3.75e+43) |

Expanding the energy range results in a slightly higher temperature, although still within the bounds of the previous fit. The emission measure finds better constraints with the low-energy count information.

{%include fitrange_comparison.html %}

Residuals in this figure are simply data - model.

## DEM solution

The joint DEM solution can now take advantage of additional counts at lower energies. The NuSTAR counts were split up into two bins, one from 2.2-3.0 keV and one from 3-4 keV. Instrumental response at the energies is different, as seen by the temperature response matrix.

With the minimum error threshold set at 50% or higher, DEMreg manages to find a solution where the inputs agree relatively well with the outputs for both EUV and Xray channels. When no minimum error is set and the instrumental or counting error is used, the fit tends to favor the Xray over the EUV, resulting in a poor fit of the AIA data.

The temperature response matrix for the different channels, DEM solution and input versus output are shown below.

Compared to [previous results](https://elastufka.github.io/presentations/Joint%20DEM%20(orbit%208).slides_updated.html#/4) when using the NuSTAR counts in a single energy bin starting at 2.5 keV, there is a greater high-temperature (>6.5 MK) component than before. The majority of the EM still comes from the peak around 6.3 MK.

### Input data and errors

| Channel | Data (Average DN/s over selected region) | Error | Percent Error |
|---| ---| ---| --- |
|94 |     3.69 |  2.98 |  81 %|
|131 |     51.85  | 10.23  | 20 %|
|171 |     657.78 |  71.18 |  11 %|
|193 |     1164.38 |  121.16 |  10 %|
|211 |     518.24 |  56.06  | 11 %|
|335 |     29.28 |  5.18  | 18 %|
|Be-Thin |     9.85 |  4.93 |  50 %|
|NuSTAR 2.2-3.0 keV |    1.02  | 0.51  | 50 %|
|NuSTAR 3.0-4.0 keV |    0.11  | 0.08  | 75 %|

### DEM fit results

**chisq:** 0.841

**AIA DN_reg/DN_in ratio:** 0.865

**Xray DN_reg/DN_in ratio:** 0.938

{%include jointDEM_trmatrix.html %}

{%include jointDEM_solution.html %}

{%include jointDEM_in_v_out.html %}
