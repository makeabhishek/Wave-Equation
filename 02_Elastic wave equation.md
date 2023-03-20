# Elastic Wave Equation

The first order 2D hyperbolic elastodyanmic equations (Velocity-Stress formulation).

$$ \rho\frac{\partial v_x}{\partial t} = \Bigg(\frac{\partial \sigma_{xx}}{\partial x} +\frac{\partial \sigma_{xz}}{\partial z}+f_x \Bigg) $$

$$ \rho\frac{\partial v_z}{\partial t} = \Bigg(\frac{\partial \sigma_{xz}}{\partial x} +\frac{\partial \sigma_{zz}}{\partial z}+f_z\Bigg) $$

$$ \frac{\partial \sigma_{xx}}{\partial t} = (\lambda+2\mu)\frac{\partial v_x}{\partial x} + \lambda \frac{\partial v_z}{\partial z} $$

$$ \frac{\partial \sigma_{zz}}{\partial t} = \lambda \frac{\partial v_x}{\partial x} \ \ \ \ \ +  (\lambda+2\mu)\frac{\partial v_z}{\partial z} $$

$$ \frac{\partial \sigma_{xz}}{\partial t} = \mu\Bigg(\frac{\partial v_x}{\partial z} + \frac{\partial v_z}{\partial x}\Bigg) $$

where, $\sigma_{xx}, \sigma_{zz}$ are normal stress and $\sigma_{xz}$ is the shear stress component; $(f_x, f_z)$ are the body-force components; $\rho$ is the density; $\lambda$ and $\mu$ are Lam\'{e} coefficients, and $v$ is the velocity vector. The system of equations propagates explicitly, velocity and stress inside the medium.
