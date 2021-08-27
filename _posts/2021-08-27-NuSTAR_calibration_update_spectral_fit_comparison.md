---
title: "NuSTAR calibration update spectral fit comparison"
categories:
  - posts
tags:
  - NuSTAR
  - xspec
---

A patch to CALDB (currently in testing phase, not yet released) allows reliable fitting to lower energy ranges. New count, response, and background files for the [X-ray peak of the 20 September 2020 flare]() were generated using the patch. Fits were run with [pyXspec]( ) in two energy ranges: the original 2.5-4.5 keV and an expanded 2.2-4.5 keV range. 

Fitting with the original energy range produced identical results. None of the count values in the low energy (<2.2 keV) range were actually changed by the new calibration in this particular case.

| Energy range (keV) | T (MK)| EM (cm$^{-3}$) |
|---|---|---|
| 2.5 - 4.5 | 2.91 (2.58 - 3.3) | 7.32e+43 (0 - 2.79e44) |
| 2.2-4.5 | 3.31 (3.07 - 3.55) | 2.14e+43 (1.3e+43 - 3.75e+43) |

Expanding the energy range results in a slightly higher temperature, although still within the bounds of the previous fit. The emission measure finds better constraints with the low-energy count information.

{%include fitrange_comparison.html %}
