---
title: "Fit to NuSTAR spectrum with pyXspec example"
image: 
  path: /images/transparent_banner.png
  thumbnail: /images/fit_xspec.png
  caption:
categories:
  - posts
tags:
  - NuSTAR
  - xspec
  - examples
  - spectroscopy
---

[PyXspec](https://heasarc.gsfc.nasa.gov/xanadu/xspec/python/html/index.html#) is the Python interface to NASA's [X-ray Spectral Fitting Package](https://heasarc.gsfc.nasa.gov/xanadu/xspec/).

This example demonstrates how to fit a thermal model with coronal abundances to NuSTAR count spectra from both telescopes. It is based on the xspec script found [here](https://github.com/ianan/nustar_sac/blob/master/xspec/apec1fit_fpm2_cstat.xcm).

## Setup

If these (bash) commands are not executed at startup of the shell, execute before starting a Python or Jupyter session in that same shell.

    export HEADAS=/whereHEASOFTlives/HEASOFT/heasoft-6.29/x86_64-apple-darwin19.6.0/
    . $HEADAS/headas-init.sh
    
## Logging

PyXspec prints lots of information to the terminal. It might be easier to capture it in a log file instead of spending time sifting through the documentation to find out how to get the relevant attributes out of the objects.

    logfile = xspec.Xset.openLog("xspec.log")
    
## Input

Although the option to specify a .rmf and .arf file to the required input .pha file exists, this is only checked after the default file is searched for, which then prompts for user input. This is fine if running in the terminal, but if running in Jupyter the user can't input the correct file name. So unfortunately the default filenames must be kept.

Load multiple spectra at once using an AllData object. *Assign the spectra to different groups.* This is important because different model parameters will be applied to each spectrum! The syntax '1:1' assigns spectrum 1 to data group 1, and similarly for 2:2. If this is not included, both spectra will be assigned to the same data group 1.  

    phaA='nu80610208001A06_chu12_N_sr.pha' 
    phaB='nu80610208001B06_chu12_N_sr.pha'
    xspec.AllData('1:1 ' + phaA + ' 2:2 '+ phaA)
    
If .rmf and .arf files are located in the same folder, these will automatically be loaded.

## Plot Configuration

A lot of the output of pyXspec seems to be controlled by its plot settings. To re-iterate the previous command, set the groups to separate groups 1 and 2 (this may or may not be redundant). Disable adding of spectra for now. Don't specify a plotting device (default is Xserver) and change the x-axis units to keV.

    xspec.Plot.setGroup("1 2")
    xspec.Plot.add=False 
    xspec.Plot.device = '/null'
    xspec.Plot.xAxis = "keV"

## Specifying Coronal Abundances

Set the abundances to coronal solar abundances by specifying the location of the file.

    xspec.Xset.abund="file %s" % abundf
    
## Model Set-up

The model can be chosen from any of the XSPEC models. The one used here is constant \* apec, so a thermal model. Make sure to use Cash statistics.

    xspec.Fit.statMethod = "cstat"
    m1=xspec.Model('const*apec')

### Controlling model parameters
    
This is important when using both spectra at the same time. Set the constant parameter of the first model (telescope A) to a default value of 1 and allow steps in increments of 0.1.
    
    m1.setPars({1:"1.0 -.1"})
    
The two constant*apec models are by default tied to each other, ie, they have the same parameter values. To allow the constant of the telescope B model, which has a different response to telescope A, to vary, detach this component from the model using untie() with the selected model and parameter. Allow the parameter to vary by unfreezing it.

    m2=xspec.AllModels(2)
    p6=m2(1)
    p6.untie()
    p6.frozen=False

To freeze a specific model parameter, set frozen = True. As an example, the temperature parameter of the first model (telescope A), whose name in the apec model is kT, is frozen.

    par=getattr(m1.apec,'kT')
    vals=par.values
    vals[0]=freezevalue*fac
    svals=[str(v) for v in vals]
    newvalues=",".join(svals)
    par.values=newvalues
    par.frozen=True

## Fit Range

When specifying the energy range to fit over, make sure to use floats. Otherwise the units will be in XSPEC channels, an index.

    xspec.AllData.ignore("0.-2.5 4.5-**")
    
This ignores everything outside the desired 2.5-4.5 keV fit range.

## Fit data to the model
Disable user prompts using the first command (not necessary if running from terminal). Fit.renorm() renormalizes the model parameters after any tweaking, so good to run just in case. Finally, set the number of iterations and perform the fit. 

    xspec.Fit.query = "no"
    xspec.Fit.renorm()
    xspec.Fit.nIterations=1000
    xspec.Fit.perform()

## Calculate Errors
Get the 1.0-sigma error for model parameters 2,5, and 6 (kT, norm, and telescope 2 constant). Here the parameter named norm reperesents the emission measure.

    xspec.Fit.error("1.0 2 5 6")

## Export results

It might be faster just to get the results from the log files, but here's an example to get out the parameters of interest and their confidence intervals. 

    kev2mk=0.0861733
    emfact=3.5557e-42
    c2=m1.apec
    T=c2.kT.values[0]/kev2mk
    T_lbound=c2.kT.error[0]/kev2mk
    T_ubound=c2.kT.error[1]/kev2mk
    EM=c2.norm.values[0]/emfact
    EM_lbound=c2.norm.error[0]/emfact
    EM_ubound=c2.norm.error[1]/emfact
    m2=xspec.AllModels(2).constant
    FPMB_fac=m2.factor.values[0]
    FPMB_lbound=m2.factor.error[0]
    FPMB_ubound=m2.factor.error[0]
    
For plotting, it would be nice to include data counts outside of the fit range. The fit range can be expanded, again using floats if units given in keV.

    xspec.AllData.notice("2.0-5.0")

Finally, to export the data and the model fit, we need to first group the data together. The slight change in syntax to setGroup makes a big difference! We need to enable addition of the spectra as well. 

    xspec.Plot.setGroup("1-2") 
    xspec.Plot.add=True
    
To export the data, call the XSPEC plot commands. It won't automatically overwrite files, so be aware of that. The result is a text file with three header rows then data in five columns corresponding to: energy, energy error,data,data_err,and model. Examples for reading the data into pandas then plotting with plotLy are linked below.

    xspec.Plot.addCommand(f'wd {xspec_out.txt}')
    xspec.Plot.iplot('ldata', 'ufspec', 'delchi')


### Notebook & Code

An [example notebook](https://github.com/elastufka/solar_all_purpose/blob/main/pyXspec%20test.ipynb) including plotted results and pyxspec [fitting class](https://github.com/elastufka/solar_all_purpose/blob/main/fit_with_xspec.py) are available.
