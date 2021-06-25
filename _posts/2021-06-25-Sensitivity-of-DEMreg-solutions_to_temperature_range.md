---
title: "Sensitivity of DEMreg solutions to temperature range"
categories:
  - posts
tags:
  - AIA
  - XRT
  - NuSTAR
  - DEM
---

The shape of joint DEM solutions (AIA + Xray) provided by [DEMreg](https://github.com/ianan/demreg) are very sensitive to the upper boundary of the selected temperature range. 

This was run using the updated version of DEMreg (18.6.21), which defaults to using EM loci minima as the initial solution.

Key inputs to [joint_DEM()](https://gitlab.fhnw.ch/erica.lastufka/small-nustar-flare/-/blob/master/joint_dem.py), otherwise using default parameters for orbit 8:

```python
tr=["2020-09-12T20:39:00","2020-09-12T20:42:00"]
tstart=5.0
tend=np.linspace(6,7.3,14)

for t in tend:
    foo=joint_DEM(timerange=tr,tstart=tstart,tend=t,numtemps=50)
    foo.xrt_submap_radius=5
    foo.aia_contour=70
    fdf=foo.run_from_inputs()
```

| aia_contour (%) | aia_area (cm<sup>2</sup>) | xrt_submap_radius (arcsec) | xrt_area (cm<sup>2</sup>) | nustar_submap_radius (arcsec) | xrt_fac | nustar_fac | 
| --- | --- | --- | --- | --- | ---| ---|
|70 | 2.49e+16 | 5 | 5.41e+17 | 55 | 1| 1|

## Results

{%include DEMreg_temp_dem.html min-height="800px"%}

{%include DEMreg_temp_dnreg_v_dnin.html min-height="800px" %}

Depending on where the temperature axis is cut off, the shape of the DEM changes. Low-temperature cutoffs (< log<sub>10</sub> T = 6.5) result in fits that don't pay much attention to the X-ray data, as might be expected. Large outliers for both NuSTAR and XRT in the DN_reg vs DN_in plot confirm this. 

However, if the temperature range goes too high (> log<sub>10</sub> T = 6.9) the shape of the DEM once again wants to trend supriously upwards, giving too much weight to the X-ray contriubutions and drastically changing the result of the DEM solution. 

From this, _tend_=6.9 is the optimal upper limit to the temperature axis, which includes the high energies in the solution without weighting their importance too the extreme.
