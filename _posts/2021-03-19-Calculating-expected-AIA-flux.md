---
title: "Calculating Expected AIA flux"
categories:
  - posts
tags:
  - AIA
  - calculation
---

To calculate expected flux (per AIA pixel) given a temperature and emission measure (_expected_AIA_flux() in _flare_physics_utils.py_):

<math>F = EM/R(T) </math>

where F is the flux in units DN s<sup>-1</sup> px<sup>-1</sup>, EM has units (cm<sup>-3</sup>) and R(T) is the response fuction of a given channel at a given temperature, in units DN cm<sup>5</sup> s<sup>-1</sup> px<sup>-1</sup>.

The response function on a given day can be obtained with _sswidl_'s _get_aia_response.pro_ .

To properly calculate the pixel size, use the Sun-Earth distance on the date in question (see _arcsec_to_cm()_ in _sunpy_map_utils.py_): angular_diameter_arcsec=radians_to_arcseconds * diameter/distance. One square AIA pixel will be about 5.36×10<sup>17</sup>cm<sup>2</sup>.

Divide the response function at temperature log<sub>10</sub> T (MK) by this pixel area. Units of R(T)/pixel_area are: DN cm<sup>3</sup> s<sup>-1</sup>, which means the units of the predicted flux are now simply DN s<sup>-1</sup>.  

Given observed fluxes, the EM can also be calculated from the above equation (see _EM_loci_curves()_ in _flare_physics_utils.py_)

## Examples 

```python
obs_params['EM_spec_cm-3']=1.03e43
obs_params['EM_err_cm-3']=[7.17e42,1.32e43]
obs_params['T_spec_MK']=3.244
obs_params['T_err_MK']=[3.195,3.347]
```

obstime='2020-09-12 20:51:00'
testfluxes=get_datavec(df, pd.to_datetime(obstime))
argmax2D(testfluxes[4]) #211

obs_fluxes=[f[33,32] for f in testfluxes] #Now it's a random point
obs_fluxes

[6.198385031134314,
27.573456549919502,
498.955343496757,
1216.220135844588,
398.1122242168047,
5.860411883536379]

print(argmin2D(testfluxes[4]))
outside_fluxes=[f[1,45] for f in testfluxes]
outside_fluxes

[0, 45]

[1.1825562246404253,
 2.7573456549919504,
 191.98281753783036,
 78.0141205558206,
 13.09806451968708,
 0.3447301107962576]
 
 

{%include AIA_predicted_vs_obs_brightest.html %}

{%include AIA_predicted_vs_obs_dim.html %}


### References 

matej's paper

Boerner, P. F., Testa, P., Warren, H., Weber, M. A., & Schrijver,
C. J. 2014, Sol. Phys., 289, 2377'''

