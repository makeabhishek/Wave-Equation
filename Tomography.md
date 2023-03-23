# Tomography

Tomography is derived from the Greek word “tomos”, meaning “slice”. 

Forward problem is used to obtain the data ('d' time traces) from the structure ('m', velocity or material property). 
On the other hand, tomography is an inverse problem to obtain image or model parameters ('m', velocity) from the data (time traces or a-scans) by combining the slices.

## ray-based traveltime tomography

Ray theory is based on high-frequency approximation:

$$\Delta T = \int_{Ray} s dl$$

In ray-based traveltime tomography, the geometry is formulated from the ray paths and invert for the model parameters (m) that defines the structure.
$$d=Gm$$
$$m_{est} = [G^T G]^{−1}[G^T d]$$

where, $d, m, G$ are the vectors containing the data, the model parameters and the kernel which maps the data into the model and vice-versa. If there are $N$
number of data and $M$ number of model parameters then the size of the matrix $G$ is $N*M$.

Above inverse problem can be formlated as least squares (LSQ) with regularisation

$$m_{est} = [G^T G + \lambda L(m)]^{−1}[G^T d]$$

## Finite-frequency traveltime tomography
In this we say that the traveltime residual $(\Delta T)$ is not only sensitive to the slowness along the ray but it also considers a volumetric region around the ray. So instead of thin ray its a volumetric kernel.

$$$\Delta T = \int_{V} K_m(**x**) d ln m(**x**)$$

where, $K_m$ is the kernel
