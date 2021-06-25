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

Key inputs to [joint_DEM()](https://gitlab.fhnw.ch/erica.lastufka/small-nustar-flare/-/blob/master/joint_dem.py), otherwise using default parameters for orbit 8 :

```python
tr=["2020-09-12T20:39:00","2020-09-12T20:42:00"]
tstart=5.0
tend=np.linspace(6,7,11)

for t in tend:
    foo=joint_DEM(timerange=tr,tstart=tstart,tend=t,numtemps=50)
    foo.xrt_submap_radius=5
    foo.aia_contour=70
    fdf=foo.run_from_inputs()
```

| aia_contour (%) | aia_area (cm^2) | xrt_submap_radius " | xrt_area (cm^2) | nustar_submap_radius " | xrt_fac | nustar_fac | 
| --- | --- | --- | --- | --- | ---| ---|
|70 | 2.49e+16 | 5 | 5.41e+17 | 55 | 1| 1|

## Results

{%include DEMreg_temp_dem.html min-width="800px"%}

{%include DEMreg_temp_dnreg_v_dnin.html min-width="800px" %}

From this, _tend_=6.9 was chosen...
