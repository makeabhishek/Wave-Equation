# Introduction
## Function and operators:

### Function: $R^{d1} \rightarrow R^{d2}$, maps between vector spaces
Function is a mathematical struture that maps between vector spaces,
Example:
  + let $f_1(x) = sin(x)$; for $x \in R$ \
        $z=f_1(x) = sin(x) \in [0:1]$. It means if we input N, real number (R), than we will get the numbers between 0 and 1. \
In other words $f_1$ maps $R \rightarrow[0,1]$. It means a function takes a number and output another number. \
  + universal apprixmation theorem
  + Image classification

### Operator: mapping from one function to other function. 
  + maps between infinite-dimensional function space: function ($\infty$-dim) \rightarrow function($\infty$-dim) or $G(f_1(x)) = f_2(x)$ \
Example: \
  + Derivative operator $\rightarrow \frac{d}{dx}$ (local): It transforms a function $f_1$ into a funciton $f_2$:
      + Let $f_1(x) = sin(x)$ then we apply operator: $f_2=\frac{d f_1(x)}{dx}=\frac{d}{dx}sin(x)=cos(x)$, which is a funciton. \
      + $x(t)\rightarrow x'(t)$. mapping one fucntion to other function.
  + Integral (global): $x(t) \rightarrow \int K(s,t) x(s)ds$, this is integral of x with respect to kernel K. Here, $K(s,t)$ is kernel,

### Why do we need to study operators
Lets assume a Burgers equation
$\frac{\partial u}{\partial t} + u\frac{\partial u}{\partial x} = v\frac{\partial^2 u}{\partial x^2}$ \
$x \in [-1,1]$ and $t \in [0,1]$ ; diffucion coefficient $\nu = 0.01/ \pi$. If we change the parameter there willl be different problem. So is there a way to make this general, which can be implement for any problem. It can be done by operator, for example derivative operator, which takes the function and perform operation.

## Integral equations: 
  + An integral equation is an equation in which an unknown function to be detemrined under one or more integral sign. If the derivative of function are involved, it is called an **intero-differential equation**. An equation of the form: \
  + $v(s)\cdot u(x) = f(x) + \lambda \int_{a} k(x,t) u(t)dt$ is called Linear Integral equation, where upper limit may be either variabkle $x$ or fixed and $u(x)$ is unknown function $v(x), f(x)$ and the kernel of the integral equation $k(x,t)$ are known fucntion; $\lambda$ is a non-zero or complex parameter. \

### Types of Integral Equation
  (i) When $v(x)=0$, then equation reduces to $f(x) + \lambda \int_{a} k(x,t) dt =0$, whcih is known as Linear integral equation of the first kind \
  (ii) When $v(x) =1$, then equation reduces to $u(x) = f(x) + \lambda \int_a k(x,t)u(t) dt$, which is known as Linear integral equation of the Second kind. \ 
  + Further if in above integral equation upper limit is variable (for example $\int_{a}^{x}$) and lower limit is constant, then these equations are called **Volterra equation** of 1st and 2nd kind. On the other hand if both upper limit and lower limits are constant (example $\int_{a}^{b}$), it is known as **Fredholm interal equation** of 1st and 2nd kind. 
 + When $f(x) =0$ in above equations, these are called **homogeneous integral equations**. 
 
 ### What does "kernel" represent in integral kernel?
  + In algebra, the term kernel of a homomorphism refers to the inverse image of the zero element. In functional analysis, there is the term "integral kernel". Examples are Possion kernel, Dirichlet kernel etc. \
  + In simple language it denotes the inner part. According to dictionary, kernel is "the important, central part of anything". (This is the third meaning in Chambers Concise Dictionary). From O.E. cyrnel=corn,grain + dimin. suffix -el). \
  + An integral kernel is, of course, **an integrable generalization** $𝐾(𝑥,𝑦)$ of a matrix $𝑀_{𝑗,𝑘}$. You could very loosely call this a "kernel" in the sense of the "core" of the formula for a integral linear operator.  \

#### Kerenel and Different kinds of Kernels in Integral Equations -
The function $k(x,t)$ is known as kernel of the integral equation.
  + Symmetric kernel: A kernel $k(x,t)$ is said to be symmetric or hermitian, if $k(x,t)=k(t,x)$, where $k$ stands for complex conjugate of $k$. In case of symmetric kernel $k(x,t)$, $\rightarrow k(x,t)=k(t,x)$
      +Example: $x^2 + t^2, (x-t)^2, sin(x+t)$, etc., are all symetric kernel. $xt^2$ is not symmetric kernel.
  + Resolvent Kernel or reciprocal kernel: $u(x) = f(x) + \lambda \int_{a}^{b}k(x,t)u(t) dt$
  + Iterated kernel: Consider Fredhold integral equation of 2nd kind $u(x) = f(x) + \lambda \int_{a}^{b}k(x,t) u(t)dt$. Then, the iterated kernels $k_n(x,t), n=1,2,3,...$ are defined as follows, $k_1(x,t)=k(x,t)$
  + Separable or Degenerate kernels: A kernel $k(x,t)$ is called separable, if it can. be expressed as the sum of a finite number of terms, each of which the product of a function of $x$ and a function of $t$ i.e., $k(x,t) = \sum_{i=1}^{n}f_i(x) g_i(t)$, where $n$ is finite and $f,g$ are linearly independent sets of funtion and $k(x,t) = \int_{a}^{b}k(x,z)k_{n-1}(z,t)dz$, n=1,2,3,...

#### Fredholm integral equation
  + A Fredholm equation is an integral equation in which the term containing the kernel function (defined below) has constants as integration limits.   + An inhomogeneous Fredholm equation of the first kind is written as \
                  $g(t)=\int _{a}^{b}K(t,s)f(s)\,\mathrm ds$ \
 and the problem is, given the continuous kernel function $K$ and the function $g$, to find the function $f$. Fredholm equations arise naturally in the theory of signal processing, for example as the famous spectral concentration problem popularized by David Slepian. The operators involved are the same as linear filters. They also commonly arise in linear forward modeling and inverse problems. \

# Sensitivity Kernel
+ The sensitivity kernel is an expression that relates a change in the acoustic field between a source and a receiver, to a local change in the medium property [1].

+ Based on the adjoint-state (or Lagrangian multiplier) method, sensitivity kernels in FWI can be constructed by cross-correlating the forward and adjoint wavefields, which avoids direct calculation of the Jacobian matrices for (very) large-scale inversion practices (Plessix 2006; Métivier et al. 2013) [2].

+ Sensitivity kernels of the coda provide the connection between a localized spatial perturbation of some propagation properties in the medium (e.g. wave speed, attenuation, scattering strength) and the changes of a certain waveform property that we observe in the coda.
+ This means the sensitivity kernels solve the forward problem of predicting the effect of a medium change on the observable and are thus a tool to localize the perturbations in the Earth based on seismogram changes [3].
+ 

**Model parameters and discretisation**
lets assume we have a square region of interest for which we want to perform inversion. 
We discretize the model into grids of 128 by 128 in the $X$ and $Y$ direction, which leads to 16,384 model parameters. 





# Useful Concepts and Definitions (misfit, adjoint sources, and kernels)
- **`Fréchet derivatives, Fréchet kernels or sensitivity kernels'**: Functional derivatives of seismic measurement with respect to structural model parameters [4]. Seismic measurement could be misfit funciton $(\chi (m))$ for the inverse problem becuase it is also a measurment (data), calcualted based on synthetic and observation data $\bigg (\frac{\partial \chi}{\partial m}\bigg )$, also called gradient of misfit function.
- **`Misfit`**: Misfit (objective) function is a metric to characterize the distance between observations and numerical calculations. Favored misfit function in exploration seismology is waveform difference. Misfit functions defines how the kernels generated, which exactly defines how model updated. 
  -  envelop misfit function
  -  Double difference misfit function
 
- **`Adjoint operator`** The adjoint operator provides an efficient way to numerically evaluate the gradient of a given misfit function
- **`Adjoint simulation`**: simulates the interaction of a forward and adjoint wavefield.
  - **`Forward wavefield`**: the seismic wavefield propagated from the source location
  - **`Adjoint wavefield`**: a wavefield that propagates from receiver locations, whos time-dependent amplitude is controlled by adjoint sources
- **`Adjoint source`**: time-reversed waveforms input at receiver locations. Typically they contain information about the forward wavefield (sensitivity kernels), or data-synthetic misfit (misfit kernel)  
- **`Kernel`**: The volumetric integration of the interaction between the forward and adjoint wavefields, highlighting regions/parameters of the model that have an effect on the wavefield or misfit  
- **'Inverse Problem'**: The problem of recovering suitable parameters (m) from a set of observations (d) is the associated inverse problem. $ G(m) = d$, where, $G$ is known as the design matrix, and a vector containing the unknowns.
- Variation of a function/total variation: A numerical characteristic of functions of one or more real variables which is connected with differentiability properties.

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









**References**

[1] Sarkar, Jit, et al. "Sensitivity kernel for surface scattering in a waveguide." The Journal of the Acoustical Society of America 131.1 (2012): 111-118.
[2] Song, Jianyong, et al. "Attenuation Sensitivity Kernel Analysis in Viscoelastic Full-Waveform Inversion Based on the Generalized Standard Linear Solid Rheology." Surveys in Geophysics (2023): 1-33.
[3] Zhang, Tuo, Christoph Sens-Schönfelder, and Ludovic Margerin. "Sensitivity kernels for static and dynamic tomography of scattering and absorbing media with elastic waves: a probabilistic approach." Geophysical Journal International 225.3 (2021): 1824-1853.
[4] Liu, Q., and Y. J. Gu. "Seismic imaging: From classical to adjoint tomography." Tectonophysics 566 (2012): 31-66.
