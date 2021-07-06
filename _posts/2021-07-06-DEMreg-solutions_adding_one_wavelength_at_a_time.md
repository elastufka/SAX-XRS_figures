---
title: "DEMreg solutions - adding one wavelength at a time"
categories:
  - posts
tags:
  - AIA
  - XRT
  - NuSTAR
  - DEM
---

The shape of DEM solutions provided by [DEMreg](https://github.com/ianan/demreg) are strongly affected at high energies by the addition of Xray data. For completeness, I added each channel (both EUV and Xray) one at a time to the inputs to see how the solution was affected. The significant results are still what happens when the Xray data is added. 

This was run using the updated version of DEMreg (18.6.21), which defaults to using EM loci minima as the initial solution.

The 70% contour of the AIA 211 peak flare to preflare difference image was used to define the selection area of all the AIA images used. The already-binned XRT maps used a selection with an approximate radius of 4", meaning that the area of the XRT image used compared to the area of the AIA image used had a ratio of roughly 7:1. DEM solutions using areas closer to equal can be seen [here](https://elastufka.github.io/presentations/Joint%20DEM%20(orbit%208).slides.html#/4), and they are quite poor. 

Results of the solutions for various configurations are in the table below. The ratios are the sum of the output data numbers (DN_reg) divided by the input data numbers (DN_in) for all AIA or Xray channels used, respectively.

|     channels  |    aia_ratio  |   xray_ratio  |  DEM chisq |
| --- | --- | --- | --- | 
|    [94]   |  0.146086  |     |   1.050238 |
|    [94, 131]   |  0.812705  |     |   0.630356 |
|    [94, 131, 171]  |   0.806346  |     | 1.075955 |
|    [94, 131, 171, 193]  |   0.891394   |    |    0.877872 |
|     [94, 131, 171, 193, 211]  |   0.886061  |      |  1.183329 |
|     [94, 131, 171, 193, 211, 335]   |  0.891701  |     |   1.231429 |
|     [94, 131, 171, 193, 211, 335, Be-Thin]  |   0.868962  |   0.996809  |   1.038052 |
|     [94, 131, 171, 193, 211, 335, NuSTAR 2.5-3.5 keV]  |   0.878576  |   1.00009  |   0.708879 |
|     [94, 131, 171, 193, 211, 335, Be-Thin, NuSTAR 2.5-3.5 keV]   |  0.385196  |   0.666093  |   15.663325 |

## DEM Solutions

{%include DEMreg_wave_dem.html min-height="800px"%}

{%include DEMreg_wave_dnreg_v_dnin.html min-height="800px" %}

Most important is the comparison between the final 4 traces: (complete) AIA-only, AIA + XRT, AIA + NuSTAR, and AIA + XRT + NuSTAR. Just adding NuSTAR forces a stricter cutoff at high temperatures than only adding XRT. Both regulate the high-temperature behaviour more than the AIA-only DEM solution.

Adding both XRT and NuSTAR (with no additional correction factor to their response functions) is problematic in this example. It results in weighting the X-ray input far more than the EUV inputs, as can be seen by the DN_in vs DN_reg plot: the NuSTAR value falls on the line while the rest are far below. 
