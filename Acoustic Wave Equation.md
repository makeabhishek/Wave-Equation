Wave generates with particle vibration. One should take a note that vibration and simple harmonic motion is not a wave. Wave only occurs when there is transfer of energy from one particle to other.

The wave equation is a second-order, linear partial differential equation (PDE) in which the $u$ (unknown: displacement or presure) satisfies:

## Acoustic Wave Equation

**The 1-D acoustic wave equation**
$$\frac{\partial^2 u}{\partial t^2}= v^2 \frac{\partial^2 u}{\partial x^2} $$
where $t$ is time, $x$ is space and $v$ is the wave speed (fixed non-negative real coefficient) [Ref](https://vitalitylearning.medium.com/solving-the-1d-wave-equation-numerical-discretization-190a92c917bc "text title").

In other words:

  + $u$ is the factor representing a displacement from rest situation.
  + $t$ represents time.
  + ${\frac {\partial ^{2}u}{\partial t^{2}}}$ is a term for how the displacement accelerates, i.e. not the speed at which the displacement is changing, but in fact the rate at which that displacement's speed is itself changing – its acceleration. 
  + $x$ represents space or position.
  + $\frac {\partial ^{2}u}{\partial x^{2}}$ is a term for how the displacement is varying at the point $x$ in one of the dimensions (like one of the axes on a graph). It's not the rate at which the displacement is changing across space, but in fact the rate at which the change itself is changing across space – its second derivative. In other words, this term shows how the displacement's changes are squashed up in a tiny surrounding area.

Using the notations of Newtonian mechanics and vector calculus, the wave equation can be written more compactly as $\ddot {u}= c^2 \nabla^2 u$

where the double dot on $\ddot {u}$ denotes double time derivative of $u$, $\nabla$ is the nabla operator, and $\nabla^2 = \nabla \cdot \nabla$ is the (spatial) Laplacian operator (not vector Laplacian):

${{\ddot {u}}={\frac {\partial ^{2}u}{\partial t^{2}}},\qquad \nabla =\left({\frac {\partial }{\partial x_{1}}},{\frac {\partial }{\partial x_{2}}},\ldots ,{\frac {\partial }{\partial x_{n}}}\right),\qquad \nabla ^{2}={\frac {\partial ^{2}}{\partial x_{1}^{2}}}+{\frac {\partial ^{2}}{\partial x_{2}^{2}}}+\cdots +{\frac {\partial ^{2}}{\partial x_{n}^{2}}}.}$

  - Furthermore, for complex cases numerical methods are prefered to solve wave equation by discretising the space and time. For example, finite difference method (FD), finite element method (FEM), spectral element method (SEM).

**The 2-D acoustic wave equation**
$$\frac{\partial^2 u}{\partial t^2}= \frac{k^2}{\rho^2}\bigg[ \rho \nabla \cdot \bigg(\frac{1}{\rho} \nabla u\bigg) \bigg] + q $$

where $\rho=\rho(x,z)$ is the density, $k=k(x,z)$ is bulk modulus, $u=u(x,z,t)$ is the pressure field, $q$ is the source function and $\nabla$ is known mathematically as _Del_ operator given by,

$$ \nabla =\sum _{i=1}^{n}{\vec {e}}_{i}{\frac{\partial}{\partial x_{i}}}=\left(\frac{\partial}{\partial x_{1}},\ldots ,{\frac{\partial}{\partial x_{n}}}\right)$$

Equation (1) expands to

The acoustic wave equation can be written in terms of the squared slowness (inverse of velocity) $m$ defined as $m(x,y)=c^{-2}(x,y)$ with $c(x,y)$ being the unknown spatially varying wavespeed, is given by:
$$m{\frac {d^{2}u(t,x,y)}{dt^{2}}}-\Delta u(t,x,y)+\eta {\frac {du(t,x,y)}{dt}}=q(t,x,y;x_{s},y_{s})$$

where, $q(t,x,y;x_{s},y_{s})$ is the seismic source, located at $(x_{s},y_{s})$ and $\eta (x,y)$ is a space-dependent dampening parameter for the absorbing boundary layer (used to absorb waves in simulation/modeling) and $\Delta$ is the Laplace operator (a second-order differential operator in the n-dimensional Euclidean space) $\Delta f = \sum _{i=1}^{n}{\frac {\partial^{2}f}{\partial x_{i}^2}}$.


**The 3-D acoustic wave equation**

## Elastic Wave Equation



# Derivation of the wave equation
  - The wave equation in 1D (one space dimension, i.e., $x$) can be derived in a variety of different physical settings. Most famously, it can be derived for the case of a _string vibrating_ in a two-dimensional plane, with each of its elements being pulled in opposite directions by the _force of tension_.

  - Another physical setting for derivation of the wave equation in one space dimension uses _Hooke's law_. In the _theory of elasticity_, Hooke's law is an approximation for certain materials, stating that the amount by which a material body is deformed (the strain) is linearly related to the force causing the deformation (the stress) [Ref](https://en.wikipedia.org/wiki/Wave_equation "text title").

  - Another way to solve the one-dimensional wave equation is to first analyze its frequency _eigenmodes_. A so-called eigenmode is a solution that oscillates in time with a well-defined constant angular frequency $\omega$, so that the temporal part of the wave function takes the form $e^{−i\omega t} = cos(\omega t) − i sin(\omega t)$, and the amplitude is a function $f(x)$ of the spatial variable $x$, giving a separation of variables for the wave function
 
