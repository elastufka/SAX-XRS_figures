---
title: "Displaying SunPy maps with PlotLy"
image: 
  path: /images/transparent_banner.png
  thumbnail: /images/sample_hero.jpg
  caption:
categories:
  - posts
tags:
  - SunPy
  - PlotLy
  - WCS
---

PlotLy lacks matplotlib's projections function, which allows the user to add custom coordinates to their maps using transforms. In order to use solar maps in PlotLy and Dash, these transforms have to be applied (or faked!) elsewhere.  

Notably:
- Axis limits must be given in pixels, based on desired limits in the map's WCS
- Axis tick values must be given in pixels, based on desired limits in the map's WCS
- Axis tick labels must be given in WCS
- Hovertext coordinate values must be given in WCS

This is implemented in [fake_maps_plotly.py](https://raw.githubusercontent.com/elastufka/solar_all_purpose/main/fake_maps_plotly.py). 

An example AIA map rendered as a PlotLy heatmap is shown below. The code that generates it as as follows:

```python
foo=fake_map(aia_masked,binning=8)
foo.plot_fake_heatmap(log=True,zmin=1.5,zmax=2.5)
```

where the input is a Sunpy Map with off-limb pixels masked.

{%include fake_aia_heatmap.html %}
