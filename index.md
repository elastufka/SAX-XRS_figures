# GOES-class Estimation for Behind-the-limb Solar Flares Using MESSENGER SAX

_E. Lastufka (FHNW/ETHZ) and S. Krucker (FHNW/UC Berkeley)_

Published in [ApJ](url), or read the pre-publicatation article on [arxiv.org](test2) 

## Figure 1

The soft X-ray instrument normalized response functions (above) and the MESSENGER data set of ~650 flares (below), represented by the spectra at the flare peak. The flare of 1 June, 2007, which is shown in additional detail in Figure 1 of [Dennis 2015](url), is highlighted in red. The range from 2.5-7.5 keV is used in Section 2.2 to fit the MESSENGER spectra.

{% include SXR_instr_response.html %}
{% include all_Mess_spectra.html %}

## Figure 2

Locations of flares as given by HEK/AIA. Flares are color-coded according to the ratio of the theoretical GOES flux calculated from the MESSENGER temperature and emission measure to the actual GOES flux (see Figure 4 -- MESSENGER/GOES < 1 is cyan and >1 is magenta) and the size of the symbol associated with them is directly proportional to the value of the ratio. Events marked with a plus sign indicate those where the measured GOES flux is less than class C2, corresponding to the red triangles in Figure 4.

{% include all_flare_locations.html %}


## Figure 3

Relationship of MESSENGER peak flux to GOES peak flux, for events visible to both satellites. The lines of best fit above a lower threshold (C2 for GOES long, B2 for GOES short) are also shown.

{% include direct.html %}

## Figure 4

Events which were excluded from the samples above in Figure 3. Although jointly visible to MESSENGER and GOES, events marked in red were deemed unsuitable for other reasons, described in the text.

{% include outliers.html %}

## Figure 5

Relationship of GOES-equivalent flux derived from the MESSENGER spectra to the measured GOES flux, for all jointly observed flares above a certain flux threshold (C2 for GOES long, B2 for GOES short). The blue shows the line of best fit, while the dashed black line is the 1:1 ratio.

## Figure 6

Temperatures and emission measures calculated for each instrument. MESSENGER values were obtained via OSPEX fit, while GOES quantities were calculated using the SSWIDL routine _goes_teem.pro_, based on empirical data.

## Figure 7

Comparison of SXR fluxes with EUV flux. Lines of best fit are shown in blue. In the top plot, the dashed line indicates the fit found in \citet{nittaSoftXrayFluxes2013} and begins at the value above which the fit is best (GOES M5.5 or 4x10$^6$ photons/s in EUV 195 \AA). In the middle plot, it illustrates the derived MESSENGER proxy (Equation \ref{eq:Mproxy}), after conversion via the EUV-GOES proxy (Equation \ref{eq:nitta}). In the bottom plot, the dashed line indicates the 1:1 ratio.



