---
title: "SunPy colormaps in PlotLy"
image: 
  path: /images/transparent_banner.png
  thumbnail: /images/cmaps_hero.jpg
  caption:
categories:
  - posts
tags:
  - SunPy
  - PlotLy
---

Solar image data has its own special set of colorscales associated with it. Certain instruments and wavelengths are by default presented in these scales, making their identification quick by the trained eye. SunPy has implemented most of these colormaps in its visualization.colormaps module. To use them in PlotLy, simply convert the LinearSegmentedColorscales to rgb values and add intervals to use them as PlotLy colorscales.

This is implemented in [color_tables_plotly.py](https://github.com/elastufka/solar_all_purpose/blob/main/color_tables_plotly.py). 

Available colormaps are shown below.

{%include sunpy_colormaps.html %}

Here are some examples, showing AIA images of solar flares in their native colormaps, using [my implementation of solar maps in PlotLy](https://elastufka.github.io/SAX-XRS_figures/posts/2021/09/15/Displaying_sunpy_maps_with_PlotLy.html).

{%include aia_flare_plotly.html %}

The time it takes to generate and display the plot is longer than matplotlib's, and saving the plots results in very large html files.
