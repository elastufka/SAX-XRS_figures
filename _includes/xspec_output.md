**1 spectrum  in use**
 
Spectral Data File: stx_spectrum_20210908_1712.fits{13}  Spectrum 1

Net count rate (cts/s) for Spectrum:1  2.348e+04 +/- 2.074e+01

 Assigned to Data Group 1 and Plot Group 1
 
  Noticed Channels:  1-29
  
  Telescope: Solar Orbiter Instrument: STIX  Channel Type: PI
  
  Exposure Time: 58.56 sec
  
 Using fit statistic: chi
 
 Using Response (RMF) File            stx_srm_20210908_1712.fits for Source 1
 

 Solar Abundance Vector set to file:  User defined abundance vector / no description specified
Fitting with single thermal model initially over range 2.0-10.0 keV

========================================================================

Model apec<1> Source No.: 1   Active/On

|Model| Model| Component|  Parameter|  Unit |    Value|
|---|---|---|---|---|---|
 |par|  comp| | | |
|   1 |   1 |  apec  |     kT  |       keV |     1.00000    |  +/-  0.0|          
|   2  |  1 |  apec  |     Abundanc |   |        1.00000 |     frozen|
|   3  |  1 |  apec  |     Redshift |      |     0.0        |  frozen|
|   4  |  1 |  apec  |     norm |          |     1.00000 |     +/-  0.0|          

Reading APEC data from 3.0.9


Fit statistic  : Chi-Squared              1.328790e+06     using 29 bins.

Test statistic : Chi-Squared              1.328790e+06     using 29 bins.

Null hypothesis probability of 0.000000e+00 with 27 degrees of freedom
 
 Current data and model not fit yet.

No channels ignored (no channels in specified range)

24 channels (6-29) ignored in spectrum #     1

Fit statistic  : Chi-Squared                998363.0     using 5 bins.

Test statistic : Chi-Squared                998363.0     using 5 bins.
Null hypothesis probability of 0.0e+00 with 3 degrees of freedom
Current data and model not fit yet.

### After first fit

Model apec<1> Source No.: 1   Active/On

|Model| Model| Component|  Parameter|  Unit |    Value|
|---|---|---|---|---|---|
 |par|  comp| | | |
|   1  |  1 |  apec    |   kT |        keV |     1.79174  |    +/-  4.62000E-03  |
|   2  |  1 |  apec   |    Abundanc   | |        1.00000  |    frozen |
|   3  |  1 |  apec  |     Redshift     | |      0.0   |       frozen |
|   4 |   1 |  apec |      norm         | |      9.52623E+05 | +/-  7654.01 |     


Fit statistic  : Chi-Squared                  561.79     using 5 bins.

Test statistic : Chi-Squared                  561.79     using 5 bins.

 Null hypothesis probability of 1.93e-121 with 3 degrees of freedom
 
**Single thermal fit took 0.491 seconds**

========================================================================

Model apec<1> + thick2<2> Source No.: 1   Active/On

|Model| Model| Component|  Parameter|  Unit |    Value|
|---|---|---|---|---|---|
 |par|  comp| | | |
|   1  |  1  | apec  |     kT  |       keV |     1.79000  |    frozen|
|   2  |  1  | apec  |     Abundanc  | |         1.00000 |     frozen|
|   3  |  1  | apec  |     Redshift     | |      0.0    |      frozen|
|   4  |  1  | apec   |    norm          | |     9.52623E+05 | frozen|
|   5  |  2  | thick2  |   a0      |  1e-35  |  100.000   |   +/-  0.0   |       
|   6  |  2  | thick2  |   p         | |         4.00000    |  +/-  0.0        |  
|   7  |  2  | thick2  |   eebrk    |  keV  |    16.7000  |    +/-  0.0   |       
|   8  |  2  | thick2  |   q           | |       6.00000   |   +/-  0.0          |
|   9  |  2  | thick2  |   eelow    | keV   |   3.40000  |    +/-  0.0     |     
|  10  |  2 |  thick2  |   eehigh   |  keV  |    3200.00  |    +/-  0.0    |      
|  11  |  2 |  thick2  |   norm     | |          1.00000    |  +/-  0.0        |  

**New model: single thermal fit with previous fit parameters (kT=1.79, norm=952622.80) plus thick target model initially over range 10.0-30.0 keV**

Fit statistic  : Chi-Squared              5.996501e+07     using 11 bins.

Test statistic : Chi-Squared              5.996501e+07     using 11 bins.
 Null hypothesis probability of 0.000000e+00 with 4 degrees of freedom
 Current data and model not fit yet.

### After second fit

========================================================================

Model apec<1> + thick2<2> Source No.: 1   Active/On

|Model| Model| Component|  Parameter|  Unit |    Value|
|---|---|---|---|---|---|
 |par|  comp| | | |
 |  1  |  1 |  apec    |   kT     |    keV     | 1.79000   |   frozen|
 |  2  |  1 |  apec   |    Abundanc  | |        1.00000  |    frozen|
 |  3  |  1 |  apec    |   Redshift     | |      0.0     |     frozen|
 |  4  |  1 |  apec   |    norm    | |           9.52623E+05 | frozen|
 |  5  |  2 |  thick2  |   a0        | 1e-35  |  95.0755  |    +/-  7.76587E+06 | 
 |  6  |  2 |  thick2   |  p         |  |        4.02057  |    +/-  0.669320     |
 |  7  |  2 |  thick2  |   eebrk   |   keV  |    17.9996   |   +/-  1.47333    |  
 |  8  |  2 |  thick2  |   q         | |         5.88059   |   +/-  5.66308E-02  |
 |  9  |  2 |  thick2   |  eelow  |    keV  |    3.34427   |   +/-  9.47710E+05  |
 | 10  |  2 |  thick2  |   eehigh |    keV  |    5.09335E+05 | +/-  9.36953E+08|  
 | 11  |  2 |  thick2  |   norm | |              2.85250E-02 | +/-  -1.00000     |


Fit statistic  : Chi-Squared                 1295.61     using 11 bins.

Test statistic : Chi-Squared                 1295.61     using 11 bins.
 Null hypothesis probability of 2.98e-279 with 4 degrees of freedom

**Thick target fit took 18.098 seconds**

**Single thermal plus thick target model fit over range 3.0-30.0 keV, all parameters free**

### After final fit

========================================================================

Model apec<1> + thick2<2> Source No.: 1   Active/On

|Model| Model| Component|  Parameter|  Unit |    Value|
|---|---|---|---|---|---|
 |par|  comp| | | |
 |  1  |  1 |  apec    |   kT |        keV   |   1.79000 |     +/-  0.141548|     
 |  2  |  1 |  apec    |   Abundanc  | |         1.00000 |     frozen|
 |  3  |  1 |  apec    |   Redshift      | |     0.0     |     frozen|
 |  4  |  1 |  apec    |   norm          | |     9.37035E+05 | +/-  2.97826E+05|  
 |  5  |  2 |  thick2  |   a0   |      1e-35  |  95.0779  |    +/-  2.64005E+07 | 
 |  6  |  2 |  thick2  |   p      | |            4.02055 |     +/-  3.44348      |
 |  7  |  2 |  thick2  |   eebrk  |    keV   |   18.4142   |   +/-  5.73387  |    
 |  8   | 2 |  thick2  |   q         | |         5.88056  |    +/-  0.173404     |
 |  9   | 2 |  thick2  |   eelow  |    keV  |    3.34430    |  +/-  3.03023E+05  |
 | 10  |  2 |  thick2  |   eehigh |    keV |     6.59341E+04 | +/-  6.31369E+06|  
 | 11  |  2 |  thick2  |   norm   | |            2.80595E-02 | +/-  1.09979E+04  |


Fit statistic  : Chi-Squared                 1153.91     using 11 bins.

Test statistic : Chi-Squared                 1153.91     using 11 bins.
 Null hypothesis probability of 2.70e-251 with 2 degrees of freedom

**Thermal + thick target fit took 26.880 seconds**

Chisq: 1153.914

