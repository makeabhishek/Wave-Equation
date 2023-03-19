Wave generates with particle vibration. One should take a note that vibration and simple harmonic motion is not a wave. Wave only occurs when there is transfer of energy from one particle to other.

The wave equation is a second-order, partial differential equation (PDE) in which the $u$ (unknown: displacement or presure) satisfies:

**The 1-D acoustic wave equation**
$$\frac{\partial^2 u}{\partial t^2}= v^2 \frac{\partial^2 u}{\partial x^2} $$
where $t$ is time, $x$ is space and $v$ is the wave speed.

Wave equation can be solved numerically by space and time discretisation,

**The 2-D acoustic wave equation**
$$\frac{\partial^2 u}{\partial t^2}= \frac{k^2}{\rho^2}\bigg[ \rho \nabla \cdot \bigg(\frac{1}{rho} \nabla u\bigg) \bigg] + q $$

where $\rho$=\rho(x,z)$ is the density, $k$=k(x,z)$ is bulk modulus, $u$=u(x,z,t)$ is the pressure field, $q$ is the source function and $\nabla$ is a _nabla_ s known mathematically as _Del_ operator given by,

$$ \nabla =\sum _{i=1}^{n}{\vec {e}}_{i}{\frac{\partial}{\partial x_{i}}}=\left(\frac{\partial}{\partial x_{1}},\ldots ,{\frac{\partial}{\partial x_{n}}}\right)$$

Equation (1) expands to

The acoustic wave equation can be written in terms of the squared slowness (inverse of velocity) $m$ defined as $m(x,y)=c^{-2}(x,y)$ with $c(x,y)$ being the unknown spatially varying wavespeed, is given by:
$$m{\frac {d^{2}u(t,x,y)}{dt^{2}}}-\Delta u(t,x,y)+\eta {\frac {du(t,x,y)}{dt}}=q(t,x,y;x_{s},y_{s})$$

where, $\Delta$ is the Laplace operator, $q(t,x,y;x_{s},y_{s})$ is the seismic source, located at $(x_{s},y_{s})$ and $\eta (x,y)$ is a space-dependent dampening parameter for the absorbing boundary layer.

**The 3-D acoustic wave equation**
