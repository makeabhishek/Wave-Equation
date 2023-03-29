# Useful Concepts and Definitions (misfit, adjoint sources, and kernels)
- _`Fréchet derivatives, Fréchet kernels or sensitivity kernels'_: Functional derivatives of seismic measurement with respect to structural model parameters [4]. Seismic measurement could be misfit funciton $(\chi (m))$ for the inverse problem becuase it is also a measurment (data), calcualted based on synthetic and observation data $\bigg (\frac{\partial \chi}{\partial m}\bigg )$, also called gradient of misfit function.
- _`Misfit`_: Misfit (objective) function is a metric to characterize the distance between observations and numerical calculations. Favored misfit function in exploration seismology is waveform difference. Misfit functions defines how the kernels generated, which exactly defines how model updated. 
  -  envelop misfit function
  -  Double difference misfit function
 
- _`Adjoint operator`_The adjoint operator provides an efficient way to numerically evaluate the gradient of a given misfit function
- _`Adjoint simulation`_: simulates the interaction of a forward and adjoint wavefield.
  - _`Forward wavefield`_: the seismic wavefield propagated from the source location
  - _`Adjoint wavefield`_: a wavefield that propagates from receiver locations, whos time-dependent amplitude is controlled by adjoint sources
- _`Adjoint source`_: time-reversed waveforms input at receiver locations. Typically they contain information about the forward wavefield (sensitivity kernels), or data-synthetic misfit (misfit kernel)  
- _`Kernel`_: The volumetric integration of the interaction between the forward and adjoint wavefields, highlighting regions/parameters of the model that have an effect on the wavefield or misfit  
- _'Inverse Problem'_: The problem of recovering suitable parameters (m) from a set of observations (d) is the associated inverse problem. $ G(m) = d$, where, $G$ is known as the design matrix, and a vector containing the unknowns.
- Variation of a function/total variation: A numerical characteristic of functions of one or more real variables which is connected with differentiability properties.
- 


 - **The adjoint state method** is a numerical method for efficiently computing the gradient of a function or operator in a numerical optimization problem. 
    - Adjoint state techniques allow the use of integration by parts, resulting in a form which explicitly contains the physically interesting quantity. An adjoint state equation is introduced, including a new unknown variable. 
    - The adjoint method formulates the gradient of a function towards its parameters in a constraint optimization form. By using the dual form of this constraint optimization problem, it can be used to calculate the gradient very fast. 
    - The name adjoint state method refers to the dual form of the problem, where the adjoint matrix $A^{*}={\overline {A}}^{T}$ is used.
    - An adjoint equation is a linear differential equation, usually derived from its primal equation using integration by parts. Gradient values with respect to a particular quantity of interest can be efficiently calculated by solving the adjoint equation. 
  - **Integration by parts** or partial integration is a process that finds the integral of a product of functions in terms of the integral of the product of their derivative and antiderivative. It is frequently used to transform the antiderivative of a product of functions into an antiderivative for which a solution can be more easily found

### Adjoint wavefield propagates adjoint sources from each receiver simultaneously (i.e., **1** adjoint simulation per event)
- Each component of each receiver therefore is capable of generating an adjoint source  
- Adjoint sources can be selectively windowed to isolate certain parts of the synthetic seismogram 
- The adjoint source will be fed in at receiver locations during an adjoint simulation  
- The resulting adjoint wavefield interacts with the forward wavefield to illuminate parts of the model that the misfit function is sensitive to  

# Sensitivity Kernel

+ The sensitivity kernel is an expression that relates a change in the acoustic field between a source and a receiver, to a local change in the medium property [1].

+ Based on the adjoint-state (or Lagrangian multiplier) method, sensitivity kernels in FWI can be constructed by cross-correlating the forward and adjoint wavefields, which avoids direct calculation of the Jacobian matrices for (very) large-scale inversion practices (Plessix 2006; Métivier et al. 2013) [2].

+ Sensitivity kernels of the coda provide the connection between a localized spatial perturbation of some propagation properties in the medium (e.g. wave speed, attenuation, scattering strength) and the changes of a certain waveform property that we observe in the coda.
+ This means the sensitivity kernels solve the forward problem of predicting the effect of a medium change on the observable and are thus a tool to localize the perturbations in the Earth based on seismogram changes [3].
+ 

**Model parameters and discretisation**
lets assume we have a square region of interest for which we want to perform inversion. 
We discretize the model into grids of 128 by 128 in the $X$ and $Y$ direction, which leads to 16,384 model parameters. 











**References**

[1] Sarkar, Jit, et al. "Sensitivity kernel for surface scattering in a waveguide." The Journal of the Acoustical Society of America 131.1 (2012): 111-118.
[2] Song, Jianyong, et al. "Attenuation Sensitivity Kernel Analysis in Viscoelastic Full-Waveform Inversion Based on the Generalized Standard Linear Solid Rheology." Surveys in Geophysics (2023): 1-33.
[3] Zhang, Tuo, Christoph Sens-Schönfelder, and Ludovic Margerin. "Sensitivity kernels for static and dynamic tomography of scattering and absorbing media with elastic waves: a probabilistic approach." Geophysical Journal International 225.3 (2021): 1824-1853.
[4] Liu, Q., and Y. J. Gu. "Seismic imaging: From classical to adjoint tomography." Tectonophysics 566 (2012): 31-66.
