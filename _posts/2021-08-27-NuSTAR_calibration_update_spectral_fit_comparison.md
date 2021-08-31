---
title: "NuSTAR calibration update spectral fit comparison"
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

The joint DEM solution can now take advantage of additional counts at lower energies. 

The temperature response matrix for the different channels, DEM solution and input versus output are shown below.

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

*chisq:* 0.841097
*AIA DN_reg/DN_in ratio:* 0.8648246134090013
*Xray DN_reg/DN_in ratio:* 0.9384611673299451

{%include jointDEM_trmatrix.html %}

{%include jointDEM_solution.html %}

{%include jointDEM_in_v_out.html %}
