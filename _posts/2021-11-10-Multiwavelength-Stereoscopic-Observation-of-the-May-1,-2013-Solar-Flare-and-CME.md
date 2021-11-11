---
title: "Multiwavelength Stereoscopic Observation of the May 1, 2013 Solar Flare and CME"
image: 
  path: /images/transparent_banner.png
  thumbnail: /images/may1_hero.png
  caption:
categories:
  - posts
tags:
  - figures
  - RHESSI
  - GOES
  - AIA
  - Odyssey
  - NORH
  - published
---

_E. Lastufka (FHNW/ETHZ), S. Krucker (FHNW/UC Berkeley), I. Zimovets (IKI), B. Nizamov (Lomonosov Moscow State University), S. White (AFRL), S. Masuda (Nagoya University) et al._

Published in [ApJ](https://doi.org/10.3847/1538-4357/ab4a0a), or read the pre-publicatation article on [arxiv.org](https://arxiv.org/abs/2012.10221). Only selected figures in this post have interactive features, otherwise they are exactly as displayed in the publication.

## Abstract

A M-class behind-the-limb solar flare on 1 May 2013 (SOL2013-05-01T02:32), accompanied by a (≈ 400 km/s) CME was observed by several space-based observatories with different viewing angles.
We investigated the RHESSI-observed occulted hard X-ray emissions that originated at least 0.1☉ above the flare site. Emissions below ≈10 keV revealed a hot, extended (11 MK, >60 arcsec) thermal source from the escaping CME core, with densities around 10<sup>9</sup> cm<sup>-3</sup>. In such a tenuous hot plasma, ionization times scales are several minutes, consistent with the non-detection of the hot CME core in SDO/AIA's 131 Å filter. 

The non-thermal RHESSI source originated from an even larger area (≈100 arcsec) at lower densities (10<sup>8</sup> cm<sup>-3</sup>) located above the hot core, but still behind the CME front. This indicates that the observed part of the non-thermal electrons are not responsible for heating the CME core. Possibly the hot core was heated by non-thermal electrons before it became visible from Earth, meaning that the un-occulted part of the non-thermal emission likely originates from a more tenuous part of the CME core, where non-thermal electrons survive long enough to became visible from Earth.
Simultaneous hard X-ray spectra from the Mars Odyssey mission, which viewed the flare on disk, indicated that the number of non-thermal electrons >20 keV within the high coronal source is ≈0.1 - 0.5\% compared to the number within the chromospheric flare ribbons. 
The detection of high coronal hard X-ray sources in this moderate size event suggests that such sources are likely a common feature within solar eruptive events. 

## Figure 1

<img src='/images/fig1new.png'>

The flare of May 1, 2013, was observed from many perspectives. This diagram imagines looking down on the ecliptic; solid vectors point towards the satellites, and dashed lines represent the half of the Sun visible from each perspective.

## Figure 2

From top-left, clockwise: The flare peak observed directly by STEREO-B 195 Å. RHESSI imaging of the flare peak at 02:33UT showed an extended non-thermal source leading a compact thermal source. No corresponding sources were visible in AIA 193 Å. However, plasma observed at 17 GHz by NoRH resembled the cooler-temperature AIA 304 Å images. The view from STEREO-A was occulted by 3° less than AIA, so it saw slightly more of the flare.

From an hour before the flare erupts, the full-disk view offered by STEREO-B shows the active region changing. During and after the flare peak, short-lived X-ray emission and longer-lived radio emission is seen. The filament eruption is seen especially well from the STEREO-A viewpoint, with EUV plasmoids stretched along the filament axis seven minutes after the peak.

<img src='/images/movie.gif'>

## Figure 3a

Lightcurves from instruments sensitive to hot plasma (top) and cooler plasma (bottom), for the same time period shown in the animated version of Figure \ref{fig:movie}. Flux was determined from an area 400" x 400" either centered on the flare (direct perspective of STEREO-B) or above the limb but in the same vertical extent (all occulted perspectives).

Each lightcurve was background-subtracted using pre-flare values and normalized relative to the flare peak.

The symbols indicate the imaging time cadence, which influences the relative timing of the peaks, especially in the bottom panel. The shading indicates the time period illustrated in further detail on the right.

{% include may1_euv_lightcurves.html %}
<br><br>

## Figure 3b

GOES, RHESSI, and HEND lightcurves. The GOES long channel, shown in linear scale (middle) shows an increase of flux corresponding to the RHESSI  emission, overlaid on a decaying slope. The direct view of HEND observed bursts before the main flare onset.

{% include may1_xray_lightcurves.html %}
<br><br>

## Figure 4

<img src='images/new_figure.png'>

Properties derived from the RHESSI SXR source (red curve, top plot). The emission measure stayed surprisingly constant, although the temperature followed the expected behaviour. The last three panels, which depended on imaging, are shown when the flare fluxes clearly exceed the flux of the on-disk source. The compact thermal source almost doubled in size as it rose above the flaring region and the solar limb. The density, calculated using a filling factor of unity, follows the temperature profile. Long iron ionization times might explain why AIA did not observe the thermal source.


## Figure 5

RHESSI and HEND photon spectra. The RHESSI photon spectrum was fit with both a single thermal component plus a broken power-law.

{% include goes_teem.html %}
<br/><br/>

## Figure 6

Time evolution of the soft 4-8 keV X-ray source. Contour levels are 50, 70 and 90\%, as is common with RHESSI imaging. SXR images, made every 45 seconds starting at 02:32UT, show that the compact source expanded as it moved upward above the flare region. 

The background images are from AIA 304 \AA, corresponding to the timestamps.

{% include TEM.html %}
<br/><br/>

## Figure 7

<img src='images/new_figure.png'>

The RHESSI HXR source is best summarized by this image. Low counts meant that a multi-step process was needed to ensure an accurate source size and position. During the flare peak, the extended HXR source lead the compact SXR source, both of which were high above the flare loop arcade but behind the CME front. Note that the CME front, likely due to projection effects and the 3-D structure of the event, appears to be located more to the north in the hotter FeXVIII image than for the cooler 193 image.

## Figure 8

<img src='images/new_figure.png'>

Non-thermal electron density (top) and collisional loss timescales (bottom) calculated for bremsstrahlung emission at different energies.

## Figure 9

<img src='images/aia_prediction_cbar.jpg'>

Left: Brightness of expected sources in AIA 131 and 94 Å, given the size, location, and electron density of the thermal X-ray source. Middle: AIA observations. Right: Pre-flare background-subtracted observed emission.

## Table 1

**Published properties of selected occulted flares**

<table>
<thead>
<tr><th>Date</th><th>Publication</th><th>Occultation</th><th>GOES</th><th>CME</th><th>30 keV </th><th>𝝉 (s)</th><th>𝜸<sub>cor</sub></th><th>𝜸<sub>chro</sub></th><th>30 keV</th><th>Size </th><th>Speed</th></tr>
<tr><th></th><th></th> <th></th> <th>obs.</th> <th>speed</th> <th>photon</th> <th></th><th></th> <th></th> <th> flux</th> <th> arcsec</th> <th>(km/s)</th> </tr>
<tr><th></th> <th></th> <th></th><th> est.</th> <th>(km/s) </th>  <th>flux</th>  <th></th> <th></th> <th></th>  <th>flare</th> <th></th> <th></th> </tr>
</thead>
<tbody>

<tr> <td>Mar 30, 1969</td><td><a href="https://doi.org/10.1086/150932">Frost & Dennis (1971)</a><br><a href=" https://doi.org/10.1038/224503a0">Badillo & Salcedo (1969)</a></td> <td>15°</td><td></td><td></td> <td>∼3</td><td>∼300</td> <td>∼2</td> <td></td><td></td><td></td><tr>

<tr><td>Dec 14, 1971</td> <td><a href="https://doi.org/10.1086/156370">Hudson (1978)</a></td> <td>25°</td><td></td><td></td> <td>0.05</td> <td>∼600</td> <td>2.1</td> <td></td><td></td><td></td></tr>

<tr><td>Jul 22, 1972</td> <td><a href="https://doi.org/10.1007/BF00153475">Hudson (1982)</a></td> <td>20°</td> <td></td><td></td> <td>0.1</td> <td>∼400</td> <td>2.5-1.8</td> <td></td><td></td><td></td></tr>

<tr><td>Feb 16, 1984</td> <td><a href="https://doi.org/10.1086/171320">Kane et al. (1992)</a></td> <td>36°</td> <td>B3</td><td></td> <td>0.4</td> <td>∼60</td> <td>3.8-2.6</td> <td>3.3</td><td>150</td><td>140°</td></tr>

<tr><td>Jun 30, 1991</td> <td><a href="https://ui.adsabs.harvard.edu/abs/1999A&A...342..575V">Vilmer et al. (1991)</a></td> <td>2±12°</td> <td>M5</td><td></td><td>10</td> <td>∼25</td> <td>2.8-2</td> <td></td><td></td><td></td></tr>

<tr><td>Apr 18, 2001</td> <td><a href="https://iopscience.iop.org/1538-4357/561/2/L211">Hudson et al. (2001)</a></td> <td>27°</td> <td>C2</td><td>2400</td><td></td> <td>30</td> <td>4.3-3.4</td> <td></td><td></td><td>20"-70"</td><td>1000</td></tr>

<tr><td>Oct 27, 2003</td> <td><a href="https://iopscience.iop.org/1538-4357/669/1/L49">Krucker et al. (2007)</a><br><a href="https://doi.org/10.1134/S1063772912100083">Vybornov et al. (2012)</td> <td>40°</td> <td>B1<br> >X1</td><td>2300</td><td>0.1</td> <td>135</td> <td>3.6-3.1</td> <td>2.3</td><td>80</td><td>200"</td><td>750</td></tr>

<tr><td>Nov 3, 2012</td> <td><a href="https://iopscience.iop.org/2041-8205/779/2/L29">Glesener et al. (2013)</a></td> <td>6°</td> <td>C5<br> X1</td><td>240</td><td>0.3</td> <td>30</td> <td>4.5</td> <td></td><td></td><td>50-100"</td><td></td></tr>

<tr><td>May 1, 2012</td> <td><a href="https://doi.org/10.3847/1538-4357/ab4a0a">Lastufka et al. (2019)</a></td> <td>30°</td> <td>B1<br> M3-7</td><td>400</td><td>0.03</td> <td>140</td> <td>3.3</td> <td>2.5</td><td>20</td><td>100"</td><td>200</td></tr>

<tr><td>Sep 1, 2014</td> <td><a href="https://doi.org/10.1051/0004-6361/201731368">Carley et al. (2017)</a><br><a href="https://doi.org/10.1007/s11207-018-1352-z">Grechnev et al. (2018)</a></td> <td>36°</td> <td>B1<br>X2</td><td>2000</td><td>0.2</td> <td>900</td> <td>2.06<sup>a</sup></td> <td>3.3</td><td>220</td><td>200"</td><td></td></tr>

</tbody>
</table>

  
  <sup>a</sup> This spectral index was derived from flux integrated over the entire flare [(Ackerman et al. 2017)](https://iopscience.iop.org/0004-637X/835/2/219), whereas 𝛾<sub>chro</sub> and the 30 keV flux quoted are for the first X-ray peak seen by HEND.

  
  ## Table 2
  
  Estimates of the number of electrons above 20 keV assuming thick target emissions from the footpoints and thin target for the extended coronal source.
  
 | Date | Thick target  _N<sub>e</sub>_ footpoints > 20 keV | Thin target _N<sub>e</sub>_ corona > 20 keV at peak |
 | --- | --- | --- | 
 |  Feb 16, 1984  | 2.5x10<sup>39</sup> | 2.5x10<sup>36</sup>|
 |  Oct 27, 2003  | 3.5x10<sup>38</sup> | 6.7x10<sup>35</sup>|
 |  May 1, 2013  | 9.4x10<sup>37</sup> | 2.0x10<sup>35</sup>|
 | Sept 1, 2014  | 2.7x10<sup>39</sup> | 7.7x10<sup>35</sup>|

