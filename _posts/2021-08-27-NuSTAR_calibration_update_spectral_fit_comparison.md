---
title: "NuSTAR calibration update spectral fit comparison"
categories:
  - posts
tags:
  - NuSTAR
  - xspec
---

A patch to CALDB (currently in testing phase, not yet released) allows reliable fitting to lower energy ranges. New count, response, and background files for the [X-ray peak of the 20 September 2020 flare](https://elastufka.github.io/SAX-XRS_figures/posts/2021/02/11/NuSTAR-small-flare-of-12-September-2020-orbit-8.html) were generated using the patch. Fits were run with [pyXspec](https://elastufka.github.io/SAX-XRS_figures/posts/2021/08/23/Fit-to-NuSTAR-spectrum-with-pyXspec-example.html ) in two energy ranges: the original 2.5-4.5 keV and an expanded 2.2-4.5 keV range. 

Fitting with the original energy range produced identical results. None of the count values in the low energy (<2.2 keV) range were actually changed by the new calibration in this particular case.

| Energy range (keV) | T (MK)| EM (cm<sup>-3</sup>) |
|---|---|---|
| 2.5 - 4.5 | 2.91 (2.58 - 3.3) | 7.32e+43 (0 - 2.79e+44) |
| 2.2 - 4.5 | 3.31 (3.07 - 3.55) | 2.14e+43 (1.3e+43 - 3.75e+43) |

Expanding the energy range results in a slightly higher temperature, although still within the bounds of the previous fit. The emission measure finds better constraints with the low-energy count information.

{%include fitrange_comparison.html %}

Residuals in this figure are simply data - model.
