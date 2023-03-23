# Sensitivity Kernel

+ The sensitivity kernel is an expression that relates a change in the acoustic field between a source and a receiver, to a local change in the medium property [1].

+ Based on the adjoint-state (or Lagrangian multiplier) method, sensitivity kernels in FWI can be constructed by cross-correlating the forward and adjoint wavefields, which avoids direct calculation of the Jacobian matrices for (very) large-scale inversion practices (Plessix 2006; Métivier et al. 2013) [2].

+ Sensitivity kernels of the coda provide the connection between a localized spatial perturbation of some propagation properties in the medium (e.g. wave speed, attenuation, scattering strength) and the changes of a certain waveform property that we observe in the coda.
+ This means the sensitivity kernels solve the forward problem of predicting the effect of a medium change on the observable and are thus a tool to localize the perturbations in the Earth based on seismogram changes [3].














**References**

[1] Sarkar, Jit, et al. "Sensitivity kernel for surface scattering in a waveguide." The Journal of the Acoustical Society of America 131.1 (2012): 111-118.
[2] Song, Jianyong, et al. "Attenuation Sensitivity Kernel Analysis in Viscoelastic Full-Waveform Inversion Based on the Generalized Standard Linear Solid Rheology." Surveys in Geophysics (2023): 1-33.
[3] Zhang, Tuo, Christoph Sens-Schönfelder, and Ludovic Margerin. "Sensitivity kernels for static and dynamic tomography of scattering and absorbing media with elastic waves: a probabilistic approach." Geophysical Journal International 225.3 (2021): 1824-1853.
