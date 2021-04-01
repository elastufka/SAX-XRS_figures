---
title: "AIA and NuSTAR loci curves"
categories:
  - posts
tags:
  - AIA
  - NuSTAR
  - calculation
---

## Orbit 6 

[NuSTAR observation of 2020-09-12, orbit 6](https://elastufka.github.io/SAX-XRS_figures/posts/2021/02/11/NuSTAR-small-flare-of-12-September-2020-orbit-6-source-2.html), with temperature and emission measure calculated by spectral fit between 17:17 and 17:19.

```python
_,o6rate,o6tresp=gen_nustar_tresp(nsid='80610206001',orbit='6',time='1717_1719')
obs_params['EM_spec_cm-3']=[1.07e44,1.07e44]
obs_params['EM_err_cm-3']=[6.62e43,1.47e44]
obs_params['T_spec_MK']=[3.264,3.264]
obs_params['T_err_MK']=[3.193,3.431]
```

{%include orbit6_locil.html %}

## Orbit 8

[NuSTAR observation of 2020-09-12, orbit 8](https://elastufka.github.io/SAX-XRS_figures/posts/2021/02/11/NuSTAR-small-flare-of-12-September-2020-orbit-8.html), with temperature and emission measure calculated by spectral fit between 20:39 and 20:42.

```python
obs_params['EM_spec_cm-3']=1.03e43
obs_params['EM_err_cm-3']=[7.17e42,1.32e43]
obs_params['T_spec_MK']=3.244
obs_params['T_err_MK']=[3.195,3.347]
```

{%include orbit8_locil.html %}

## Orbit 10

[NuSTAR observation of 2020-09-13, orbit 10](https://elastufka.github.io/SAX-XRS_figures/posts/2021/02/11/NuSTAR-small-flare-of-12-September-2020-orbit-10.html), with temperature and emission measure calculated by spectral fit between 00:08 and 00:15.

```python
_,o10rate,o10tresp=gen_nustar_tresp(nsid='80610210001',orbit='10',time='0008_0015')

obs_params['EM_spec_cm-3']=[8.46e42,8.46e42]
obs_params['EM_err_cm-3']=[0,4.34e43]
obs_params['T_spec_MK']=[3.206,3.206]
obs_params['T_err_MK']=[2.618,3.555]
```
{%include orbit10_locil.html %}

### Details

To calculate expected flux (per AIA pixel) given a temperature and emission measure see [previous post](). 

To calculate NuSTAR response functions, run the notebook [here]() with the .arf, .rmf, and .pha files associated with a given spectral fitting of an observation.


