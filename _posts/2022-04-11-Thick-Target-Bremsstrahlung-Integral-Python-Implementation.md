---
title: "Thick Target Bremsstrahlung Integral - Python Implementation"
image: 
  path: /images/transparent_banner.png
  thumbnail: /images/Thick Target Bremsstrahlung Integral - Python Implementation/hero.png
  caption:
categories:
  - posts
tags:
  - numerical integration
  - calculation
  - Python
  - PyTorch
---

An important emission mechanism for X-ray and gamma-ray astrophysics is thick-target bremsstrahlung - radiation resulting from the interaction of energetic electrons with thick-target plasma. A count spectrum measured by an instrument can be used to calculate the photon flux spectrum, assuming an isotropic electron distribution (and isotropic radiation).

## The Integral

The form of the integral chosen for numerical integration is from [](), and uses Gauss-Legendre quadrature to calculate the solution.

Photon flux at energy $$\epsilon$$ is given by:

$Flux(\epsilon) = \frac{n}{4\pi(AU)^2} \frac{1}{mc^2}\left[ \int_{lg(\epsilon)}^{lg(E_{eLow})} \frac{\sigma(\epsilon,E)\rm{v}}{dE/dt} F(E) 10^L \rm{ln(10)} dL + \int_{lg(E_{eLow})}^{{lg(E_{eBreak})}} \frac{\sigma(\epsilon,E)\rm{v}}{dE/dt} F(E) 10^L \rm{ln(10)} dL + \int_{lg(E_{eBreak})}^{{lg(E_{eHigh})}} \frac{\sigma(\epsilon,E)\rm{v}}{dE/dt} F(E) 10^L \rm{ln(10)} dL  \right]
$

As seen by the term $(AU)^2$ in the denominator, the distance from the emitting region to the detector is taken to be 1 AU. For STIX, this will mean the count spectrum used must be corrected to the 1 AU distance.

The relativistic electron-ion bremsstrahlung cross-section with Elwert correction is $\sigma(\epsilon,E)$; the electron speed is _v_, and _F(E)_ is the integrated electron flux distribution, taken to be a double power law with a high energy cutoff, _eHigh_, and a low-energy cutoff, _eLow_.

Thus, a thick-target model can be parameterized by 5 parameters: 

1. _p_ , the power-law index below the break energy _eBreak_

2. _q_ , the power-law index above the break energy _eBreak_

3. _eLow_,  the low-energy cutoff

4. _eBreak_,  the break energy in the double power law

5. _eHigh_ , the high-energy cutoff

The output of the integral is photon flux in units photons s<sup>-1</sup> keV<sup>-1</sup> cm<sup>-2</sup>. 

In Python, the integrand of each part can be expressed via the following:

```python
    def integrand(y, photon_energy, electron_dist,z=1.2, model='thick-target'):
        electron_energy=10**y
        brem_cross = bremsstrahlung_cross_section(electron_energy, photon_energy, z)
        collision_loss = emission.collisional_loss(electron_energy)
        pc = np.sqrt(electron_energy * (electron_energy + 2.0 * mc2))
        density=electron_dist.density(electron_energy)
        if model == 'thick-target':
            return 10**y*np.log(10)* density  * pc / collision_loss / ((electron_energy / mc2) + 1.0)
        elif model == 'thin-target':
            if efd:
                return 10**y*np.log(10)*electron_dist.flux(electron_energy)*brem_cross*(mc2/clight)
            else:
                return 10**y*np.log(10)*electron_dist.flux(electron_energy)*brem_cross*pc/((electron_energy / mc2) + 1.0)

 ```

The input _y_ is an array of the Gauss-Legendre points of order _n_, calculated for each integration limit from energy $\epsilon$ to _eLimit_, where _eLimit_ can be one of either _eLow_, _eBreak_, or _eHigh_. It has the shape (nBins, n). 

Photon energy is the input to the thick-target model. Fitting software such as OSPEX or XSPEC calculate this from the input count spectrum and detector response matrix. It is a vector of length _nBins_. 

Based the model parameters listed above, the broken power-law electron distribution is calculated, via _emission.BrokenPowerLawElectronDistribution_. 

Constants _mc2_ and _clight_ are their usual physical values.

The bremsstralung cross-section is the slowest calculation in the integrand, requiring ~ 44% of the time, based on the evaluation of one such integrand with _n_=8 and _nBins_=5. Comparitively, the electron density takes 17% of time and the collisional loss calculation 5%.

## Quadrature

Quadrature is reached when the relative error between two sucessive evaluations using _n_ and _n+1_ points respectively is less than the user-supplied relative error, defaulting to _rerr=1e-4_.  Should this condition not be met by the time the integral is evaluated with _n=max_N_ points, a warning flag may be returned.

In the IDL implementation, _n_ increases on base 2, starting from 2^2 and maxing out at 2^12 (_max_N=12_). 

## Implementation 1: IDL translation 

In _sswidl's_ OSPEX, the thick-target model is implemented as _thick2.pro_, with Gauss-Legendre quadrature following the FORTRAN formulation in [Numerical Recipes](). It is implemented in Python in [sunxspex's](https://github.com/sunpy/sunxspex)
_emission_ module.

Calculation of each part of the integral is vectorized for a single iteration with _n_ Gauss-Legendre points.

##  Implementation 3: numpy and scipy

Using [numpy.polynomial.legendre.leggauss()](https://numpy.org/doc/stable/reference/generated/numpy.polynomial.legendre.leggauss.html) can replace most of sunxspex's _emission.gauss_legendre()_. Points and weights must still be scaled via<sup>[1](https://en.wikipedia.org/wiki/Gaussian_quadrature#Change_of_interval)</sup>: 

$x_m = \frac{1}{2}(b+a)$

$x_l = \frac{1}{2}(b-a)$

$x_i=x_m + x_l ⊗ x_i$

$w_i = (w_i ⊗ x_l)^T $

Quadrature is then calculated via [scipy.integrate.fixed_quad()](https://docs.scipy.org/doc/scipy/reference/generated/scipy.integrate.quad.html), interatively from _n_=2 to _n_=12 as described above. 

##  Implementation 3: quadpy

[quadpy](https://github.com/sigma-py/quadpy) is fully vectorized, accepting vectors of integration limits (unlike scipy, where this is achieved using _numpy.vectorize()_ which I believe is a pre-compiled for loop). For this simple integration scheme, _quadpy.c1.gauss_legendre()_ is used. However, quadrature itself must still be calculated in a loop. Implementation is simpler as the points and weights are transformed to fit the integration limits internally.

## Implementation 4: torchquad

[torchquad](https://github.com/esa/torchquad) uses PyTorch to enable fast calculation numerical integrals via GPU. Currently, the release does not include Gauss-Legendre integration, so the work in [my fork]() is needed. 

In the future, torchquad will also be able to support Tensorflow, numpy, and JAX as well as Torch. Performance gain scales well on the GPU after ~10<sup>5</sup> evaluations. While this might not mean any speed-up for a single thick-target calculation (assuming a STIX temperature response matrix with ~1500 energy bins), it would hopefully boost performance when performing spectral fits, especially combined with a tensor-based minimizer. 


## Implementation 5: C++/ROOT

This is not yet done, but could be fairly straightforward and would hopefully out-perform Python implementations. [ROOT](https://root.cern.ch/doc/master/classROOT_1_1Math_1_1GaussLegendreIntegrator.html) already has Gauss-Legendre integration available, so the most difficult part would be coding the electron distribution and bremsstrahlung cross-section functions. 

## Performance Comparison

### CPU
The table below compares the performance of the IDL version and implementations 1-4 on a 2.8 GHz Quad-Core Intel Core i7.

Input parameters are:

The figure below 

### GPU

server cpu:   Intel(R) Xeon(R) CPU E5-2690 v4 @ 2.60GHz

The table below compares implementations 1-4 on [whatever the server has], with and without a GeForce GTX 1080 Ti.

### References



