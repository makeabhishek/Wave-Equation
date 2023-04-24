# Inversion 
There are a lot of methods to obtain the velocity or from . A fundamantal method to obtain velocity of the medium is first arrival travel time tomography.
However, the resolution of first arrival traveltime tomography is restricted by the size of the first Frenel zone. The first arraival traveltime 
tomography can only reconstruct the long wavelength parts of the subsurface models. It cannot reconstruct the small parts.
The reason behind this is that we only consider pick the first arrival travel time and put them in non-linear problem to obtian velocity model. 
However, we actually ignore all the other information obtain from reflection, refraction, phase and amplitude information. We are only using the 
traveltime information of the first arraival. That is why the resolution is not good. To improve the resolution, the best option would be to consider
the whole recorded waveform. So if we are considering all the information in the non-linear inversion process. It is called full-waveform inversion.

So the aim is to obtain high resolution velocity model from the recorded time-traces. To obtain the high resoltion image, we have to solve mainly three problems:

(1) **What is an "optimal" model?** In other words, what is the model that can explain the time traces very well. Can we define some criteria, which can define a model that can fits the data very well. Once we have the criteria, next question is

(2) **How can we find the model?** What kind of optimisation that we use inorder t find this model.

(3) **Is this model unique** or are other model existing, which coluld explan the data equallly well?

## (1) What is an "optimum" model?
Lets we have some observed or experimental data, then we assume a subsurface model and we compute the synthetic/modelled data set using any numerical method, for exmaple Finite difference, finite element oand so on,
So we have two data

  (1). Observed or experimental or field data $(u_{obs})$:
  
  (2). Synthetic or modelled data $(u_{mod})$:
  
  (3). Data residue $(\delta u = u_{mod} - u_{obs})$: 
  
  <img width="401" alt="Screenshot 2023-04-16 at 12 15 37 AM" src="https://user-images.githubusercontent.com/47937684/232332519-34dd9af5-178d-43c6-ba50-f923d4827e1b.png">

So based on data residue, we can quantify how well our modelled data explain the field data. The problem with this method is that we have to visually inspect the residuals for each source-receiver pair. However, if a measure can be used to condense this data residue in some quantitative numbers.
One way to measure data residues is called $L2-norm$ (Residual Energy) of the data residual. \
So we are taking the square of all the data residue samples in data and sum them. In simple form it can be written as a scalar product. $\delta u$ is a column vector and taking its transpose means it is a row vector, and the product of $\delta u^T \delta u$ is a scalar. 

**Objective Function** $E = \frac{1}{2}\delta u^T \delta u$: 

This is the way to **condence down all the data residue into single number $E$**. If the data residue high that means the misfit between the data is also high and vice versa. 

Now, the next step is to reduce/minimise the data misfit ($\delta u$). Therefore, to find the optimum model, we have to minimise the objective function $(E)$, because once the objective function is minimised, the data residue will be minimised. This means that we have to find a model which explains the experimetnal data very well (once the misfit is reduced). 

Hence, the final aim is to minimise the objective function so that the synthetic data resembels with the experimental data. Now the question is how to minimize the objective function $(E)$ and therefore find a subsurface model that can explain the field data? 

## How to find an optimum model or minimize the objective function (E)? 
The above problme looks like an optimisation problem, It is a non-linear optimisation problem. How to approach and solve this problem. These problems are usually have very large parameter space so typically it has a dimesnion of thousands to millions. Analysisng the objective funtion in space of this huge dimention is bit complicated in this world of 3D. To understand the probelm lets restrict us to 2D in to parameter space and then evaluate the misfit fucntion in this 2D parameter sapce.

A lot of mathemticians have created a lot of test functions for numerical optimisation. The plots of associated fucntion and their minima is described in wikipidea https://en.wikipedia.org/wiki/Test_functions_for_optimization#:~:text=In%20applied%20mathematics%2C%20test%20functions,Robustness.
<img width="1403" alt="Screenshot 2023-04-17 at 10 43 33 PM" src="https://user-images.githubusercontent.com/47937684/232673557-6284670e-8333-4b2a-8e5e-224a155832b8.png">

Lets take a commonly used objecive function, known as _Rosenbrock fucntion_ also called 'banana function'. We take the 2D Rosenbrock function, \
$E = (1-x_1)^2 + 100(x_2 - x_1^2)^2$ 

**To remind that the aim is to optimize material parameters of the subsurface or undergraound, therefore subtitute:**
$x_1 \rightarrow V_p (i.e. P-wave velocity)$

$x_2 \rightarrow \rho (i.e. density)$, so the resulting Rosenbrock function will be

$E = (1-V_p)^2 + 100(\rho - V_p^2)^2$

Keep in mind though that this is seophysical non-sense. With this objective function we just want to learn that how to estimate a subsurface model by minimising the objecive function. Because the form of the objective function is known, we know where the minimum of this objective function would be. By this we can also test out numerical optimisation problem.

<img width="479" alt="Screenshot 2023-04-17 at 10 52 12 PM" src="https://user-images.githubusercontent.com/47937684/232674541-be371b1e-b757-4a6a-b93a-b3b23f5804d6.png"> 

In the above image, we can see the part of the parameter space. (Again this is a geophysical non-sense). Lets assume we have one point in the subsurface, and here we have plotted the density vs P-wave velocity. So all the points in the image resembles different models of p-wave velocity and density. Now for all these models, we can calculate the synthetic data (by solving wave equation for each V_P and density) and estimate the objective function. This simly means that take the data residue between synthetic and observed data, square them and calculate the sum over all our squared data-residues, and than we can associate for each model in the misfit function as shwon in the image, i.e. Residual energy. The color in this plot resembles differents models with different objecive funtion values. So we can see that red colours are where data residues are very high and we dont want to use, because these do not represent our field data very well. However, yellow models have a very low data resideu and thereofere can explain our data very well.  So we are interested at the minimum residue.

So in order to find this optimum model we have to miminise the objective function $E$. We can do it by simple start in the parameter space ($m_1$) which has some p-wave velocity and density as initial guess. The aim is to start from this model and reac to the subsurface model. 

(1) Start search with initial guess $m_1$

(2) Define a direction in which we want to walk inside the parameter space, which is defined by a vector $\delta m_1$; define the step length and then simply walk straight in the parameter space  until we reach model $m_2$.  So, mathematically update the model iteratively : $m_2 = m_1 + \mu_1 \delta m_1$, model is a vector becaue we have two parametes p-wave velocity and density. $\delta m_1$ denotes the direction and $\mu_1$ is the step length.  

<img width="478" alt="Screenshot 2023-04-17 at 11 10 06 PM" src="https://user-images.githubusercontent.com/47937684/232676966-61c2a441-e1c2-4df9-948d-bfcb3edf4a83.png"> 

## Big question: Which Direction $\delta m_1$ should we walk/choose?
<img width="459" alt="Screenshot 2023-04-17 at 11 11 02 PM" src="https://user-images.githubusercontent.com/47937684/232677133-fb3208c0-d6d5-49e1-8c58-d87595cae49c.png">

there would be some directin which are favourable and some should be avaoided because we cannot react to the minimum after some iterations.

**We can move in the gradient direction to reach to the minimum.**
The image shows the countour lines of the objective function. One idea would be to move in the sttepest descent direction of the objective funstion. So it is the negative gradient of the objective funtion w.r.t. two material parameters. So the intutive answer would be to walk along gradinet of the objective funetion. 

## How to find optimum search direction
We simply take a look, how the objective function in the visicinity of our intial model changes when we add a small perturbation $\delta m_1$ in any direction. Now we are assuming that these perturbations are very small, we can expand this expression in to a Taylor series. So we can approximate this by the value of the objective function at our starting point $E m_1$ plus the linear term (\delta m_1) of the Taylor series expansion, i.e. $\delta m_1 \frac{\partial E}{\partial m}_1$ and the gradient of objecive function w.r.t. material parametes plus quadratic term. In the expression $\delta m_1$ is a vector so quadratic term is written in term of transpose multiplied by second derivative of objective function w.r.t. material parameters.

$E(m_1 + \delta m_1) \approx E(m_1) + \delta m_1 \delta m_1 \frac{\partial E}{\partial m}_1 + \frac{1}{2}\delta m_1^T H_1 \delta m_{1}$ So this is a Taylor expension in multiple dimensions.

with the **Hessian** $H_{ij} = \frac{\partial^2 E}{\partial m_i \partial m_j}$.

Now, we have to find optimum search direction so, fisrt calculate the derivate of objective function w.r.t. search direction and set derivative equal to zero:

$\frac{\partial E(m_1 +m_2)}{\partial \delta m_1} = 0 + \bigg( \frac{\partial E}{\partial m} \bigg)_1 + \frac{1}{2}*2*\delta m_1 H_1 =0$. This is a basic methodology to find minimum of a function. In this case it is objective funciton and the parameter that we want to minimise is the search direction $\delta m_1$. Rearranging the equationa and multiply both side by inverted Hessian, which leads to

$\delta m_1 = - H_1^{-1} \bigg(\frac{\partial E}{\partial m}\bigg)_1$,

where $(\frac{\partial E}{\partial m})_1$ denotes the gradient direction of the objective function and $H_1^{-1}$ is the inverse Hessian matrix. So finally $\delta m_1 $ is the optimum search direction according to taylor series expansion analysis. So the optimum search direction is what we almost guess. Our guess was tht it is a negative gradient of objective funtion w.r.t. material parameters and mathemativally it is shown. However, a better search direection would be if we multiply the steepest descent with inverse Hessian. And this approach is called **Newton method**. As we can see from the Newton method figure, that we are not walking along the negative gradient direction, we are also using a little bit of the slope of the fucntion, whcih is described by the Hessian. **Newton method** $m_{n+1} = m_n - \mu_n H_n^{-1} \bigg( \frac{partial E}{\partial m}_n$ 

<img width="487" alt="Screenshot 2023-04-17 at 11 38 49 PM" src="https://user-images.githubusercontent.com/47937684/232681402-a189da88-7364-4c95-b349-be00b2f1a834.png">

So this is a resonalble aporach to mimimise the objective function from a given point in the parameter space. Now the problem with this approach is that we can calculate the graidnt of obejctive function easitly with mathematial tricks but the computation of inverse Hessian is very expensive and often the inverse Hessian is singular and we 
have to stabilise it some how. Also the Hessian is very large. So what we do is to approximate inverse Hessian by a parameter called **Preconditioning operator**.

 **Gradient method** $m_{n+1} = m_n - \mu_n P_n^{-1} \bigg( \frac{\partial E}{\partial m} \bigg)_n$.
 
 So preconditioniing should emitate the action of the Hessian. If we set Preconditioning to one, this is called **steepest descent method**. One of the issues with the steepest descent method that it has slow convergence, because it slowly propagate in  the valley, as shown below. But we can spped up this process by appropriate preconditioning operator.
 
 <img width="447" alt="Screenshot 2023-04-17 at 11 48 57 PM" src="https://user-images.githubusercontent.com/47937684/232683170-57209747-f9e8-470d-a721-9f0ab27e860a.png"> 
 
 So now we have found the numerical method from which, we can find the objective function and thereofore minimise our data residue and therefore obtain the susbsurface model. 
 
 ## Final quesiton: How to calculate the gradient ($\frac{\partial E}{\partial m}$) of Objective function w.r.t. material aprameter?
How to calculate the gradient of this Objective function w.r.t. given material aprameter for a specific forward problem? There are a lot of approach to fint the gradient of objective function and the most prominent approach is called **ajdoint state method**. There are different ways to calculate adjoint state gradient directions, for example Lagrance multipliers, frequency domain, origginally these gradients were determined by using perturbation theory, developed by trantola.

  (+) Adjoint state gradient estimation using Lagrange multipliers [Plessix,2006]
  
  (+) Adjoint state gradient estimation in frequency domain [Pratt et al./ 1998, Plessix 2006]
  
  (+) Adjoint state gradient estimation using perturbation theory [Tarantola, 2005, Mora 1987, Plessix 2006].
  
Adjoint state method is a computationally chep method to calculate the gradient and this apraoch can be applied to other fields also.
 
Unfortunatelly this Adjoint state method works for linear problem, however the real senarios are non-linear, so the adjoint state approach may not really work.

  (+) Global optimisation method can be used in non-linear case to implement FWI.
 
 # Lets consider 2D Acoustic wave equation
 We assume that we can approximate ultrasonic or acoustic wave propagation and the subsurface by the 2D acoustic wave equation. It has second derivative of pressure (P) at each subsurface points (x,z) and at each time (t) w.r.t. time. Then it has laplace operator whcih is second order spatial derivative of pressure (P) field. To describe the sub-surface medium we have material parameter (vp), whcih only depends on P-wave velocity at diffeent sub-surface points (x,z). To excite the wave, we need source term, whcih is denoted by (f) at (x,z,t). This defines how source at given space points behave over time. Therefore, with source term and velocity distribution of the subsurface we can solve the wave equation using fintie difference or fintie element method, or some other method. Furthermore, for each PDE, it need to satisfy certain initial an boundary condition.
 
 $\frac{1}{vp^2(x,z)}\frac{\partial^2 P(x,z,t)}{\partial t^2} - \Delta P(x,z,t) = f(x,z,t)$ \ 
 with
 
  (+) vp(x,z) = P-wave velocity model
  
  (+) P(x,z,t) = Pressure wavefield
  
  (+) f(x,z,t) = source term
  
  (+) $\Delta = \frac{\partial^2}{\partial x^2} + \frac{\partial^2}{\partial z^2}$ = Laplace operator
  
Additionally, we have to satisfy initial and boundary conditions. The initial conditions, how the pressure field behave at intial time: 

  (+) P(x,z,0) =0 i.e., pressure field at time zero at all spatial points is zero.
  
  (+) $\frac{\partial P(x,z,0)}{\partial t} =0$ derivative of pressure field at time zero at all spatial points is zero.
  
 Now we need the boundary condition also, how the pressure field behaves at the boundary. These can be
 
 (+) Neuman B.C.: The Neumann (or second-type) boundary condition is a type of boundary condition, named after Carl Neumann. When imposed on an ordinary or a partial differential equation, the condition specifies the values of the derivative applied at the boundary of the domain.\
 (+) Drichlet B.C.:If you take consider the wave equation on a disk D, then if we use Dirichlet boundary conditions, it means the wave function is fixed at 0 on the boundary of the disk, and if we consider the eigenvalues of the system, this can be visualized physically as a vibrating drumhead. \
 (+) Free surface B.C. \
 (+) Absorbing B.C. 
 
## Calculate gradient 
So now we want to calculate the gradient of the objective function w.r.t. material parameters. In this case it is w.r.t. P-wave velociy model at each of the sub-surface points.

**Adjoint state gradient $\frac{\partial E}{\partial m}$**
For a detailed derivaion, refer to [Plessix, 2006]

**$\frac{\partial E(x,z)}{\partial m} = - \sum_s \int_{0}^{T} q_s(x,z,T-t) \frac{\partial^2 P_s(x,z,t)}{\partial t^2}$**\
with \
  (+) m = 1/vp^2(x,z) = P-wave slowness
  
  (+) P_s(x,z,t) = forward pressure wavefield
  
  (+) $\frac{\partial^2 P_s(x,z,t)}{\partial t^2}$ = second time derivative of forward pressure wavefield at each subsurface point and at each time.
  
  (+) q_s(x,z,T-t) = adjoint pressure wavefield also at each subsurface point but the time is reversed.
 
  (+) $\sum_s$ = sum over all sources
  
  (+) T = maximum time-trace recording time
  
We can see the gradient of the objective function at each subsurface points $\frac{\partial E(x,z)}{\partial m}$ w.r.t. model/material parameter $m$ at the subsurface point. We have second time derivative of forward pressure wavefield and we are multiplying it by adjoint wavefield at each subsurface points and at each time step. Actually, we perform zero-lag cross-correlation, we simply multiply both wavefields and integrate. Then we sum over each time and sum for all sources. 

## What are forward and adjoint wavefields? 
### Forward Wavefield [P_s(x,z,t)]: This can be easily computed by solving the acoustic wave equation 

$\frac{1}{vp^2(x,z)}\frac{\partial^2 P_s(x,z,t)}{\partial t^2} - \Delta P_s(x,z,t) = f(x,z,t)$ 

$P_s(x,z,t) = 0$ and 

$\frac{\partial P_s(x,z,0)}{\partial t} =0$ 

So this is the wavefield that we get when we excite a source at a given source position. the acoustic wave is traveling from the source to the sub-surface and we can record the wavefield at each subsurface point. 

### Adjoint Wavefield [q_s(x,z,T-t)]: Adjoint wavefield is basically the equation remoins the same, we still have to solve the acoustic wave equation.

$\frac{1}{vp^2(x,z)}\frac{\partial^2 q_s(x,z,t)}{\partial t^2} - \Delta q_s(x,z,t) = f_q$

However the source is changed. Here we take a so called **Adjoint source** term and inject these adjoint source terms as new sources at the receiver positions. 

### What are adjoint source [$ f_q $]?
They consist of time-reversed data residues at the receiver positions ($r$). 
$f_q = \sum_r (P_{s,r}^{(mod)}(T-t) - P_{s,r}^{(obs)} (T-t))$

$q_s(x,z,T) = 0$ 

$\frac{\partial q_s(x,z,T)}{\partial t} =0$

So first, we are calculating forward wavefield $P_s(x,z,t)$ at each subsurface points but also at each receiver position, so we are calculating sunthetic seismogram or time traces. This synethetic data are denoted by $P_{s,r}^{(mod)}(T-t)$. For each source and receiver we have synthetic A-scan that depends on time. Now we are time reversing the A-scans means flipping the A-scans along the time axis and then we are also taking observed A-scans and flipping them in time $P_{s,r}^{(obs)} (T-t)$. Then, we subtract them, whcih results in the data residues. Finally, we inject them at receiver positions. So, the source wavelet at each receiver position, whcih is now acting as source is defined by the A-scans of the data residues. Than we have intial conditions. 

### Summary
So the differnece between the Forward and adjoint wavefield is only the source term in acoustic case. So $\frac{\partial E(x,z)}{\partial m} = - \sum_{s} \int_{0}^{T} q_s(x,z,T-t) \frac{\partial^2 P_s(x,z,t)}{\partial t^2}$ equation is the fundamental part of the waveform inverison algorithm. We need to estimate the gradient of the objective function w.r.t. model parameters at each sub-surface points. 

# Full-waveform Inversion\tomography algorithm
FWI is an iterative numerical optimisation method to mimisation of the data residue between synthetic and observed data and reconstruct high resolution image, at each iteration we have to perform follwoing six steps:

(0) We obtain the observed data $P^{obs}$

(1) For each source $f(x,z,t)$ solve the forward probelm for the current model $m_n$ to generate a synthetic dataset $P^{mod}$ (pressure wavefield at receiver positions only) and the wavefield $P^{mod}(x,z,t)$

(2) Calculate the data residual of A-scans\seismograms $\delta P = P^{mod} - P^{obs}$

(3) Generate the adjoint wavefield $q(x,z,t)$ by backpropagating the residuals from the receiver positions. In other words, inject the time-reversed data residuals at the receivers positions as source.

(4) Calculate the gradients $\frac{\partial E(x,z)}{\partial m}$ (direction) for each material parameter using gradient equation $\frac{\partial E(x,z)}{\partial m} = - \sum_s \int_{0}^{T} q_s(x,z,T-t) \frac{\partial^2 P_s(x,z,t)}{\partial t^2}$.

(5) Estimate the step length $\mu_n$ by a line search. There are different algorithms to obtain step length, one prominent one is line search algorithm.

(6) Update the material parameters using the gradient method (steepest descent method: move in negative gradient direction) $m_{n+1} = m_n - \mu_n \bigg( \frac{\partial E}{\partial m}\bigg)_n $. Once we have the optimum step length we will update the model/material parameters using the gradient method. We have model at step-length $n$, then we walk in negative gradient direction with step length $\mu_n$ and get new moel $m_{n+1}$ and do it iteratively and reach to the model with minimum value of objective function. 

# Optimisation methods 
## Numerical Optimization Algorithms
Optimization Algorithms are iterative techniques that follow the following fundamental steps: \
  (+) Initialize with a guess of the decision variables $x$,\
  (+) Iterate through the process of generating a list of improving estimates, \
  (+) check whether the terminating conditions are met, and the estimates will be probably stop at the solution point $x^*$

Most of the optimization strategies make use of either the objective function $f(x)$, the constraint functions and $g(x)$ and $h(x)$, the first or second derivatives of these said functions, information collected during previous iterations and/or local information gathered at the present point.

## Steepest Descent method
The probelem with steepest descent method is that it has slow convergence speed. If the step length is large then it can stuck in a valley. \

**How can we improve the convergence speed?**
There is a simle method called **Conjugate gradient method**

(+) Minimization of the quadratic form by using conjugate search direction instead of the steepest descent direction. It was intially developed for linear probelm (Hestenes and Stifel, 1952).

(+) Later Extended to nonlinear objective functions [Fletcher and Reeves, 1964; Polak and Riebiere, 1969]

(+) Details mathematical proofs [Nocedal and wright, 1999].

Ref: Shewchuk, Jonathan Richard. "An introduction to the conjugate gradient method without the agonizing pain." (1994).

## Linear Conjugate Gradient Method
This is an iterative method to solve large linear systems where the coefficient matrices are positive definite. This can be treated as a replacement of the Gaussian elimination method in numerical analysis. \
In the linear conjugate gradient method, the direction $\delta_j$ is a linear combination of the preceding direction $\delta\_{j-1}$ and the negative of the residual $-r\_j$. So we can write  \
$\delta\_j = \chi\_j \delta\_{j-1} - r\_j$

## Nonlinear Conjugate Gradient method 
(1) Calculate the steepest descent direction: $\Delta x_n = -\bigg(\frac{\partial E(x,z)}{\partial m} \bigg)$

(2) Compute the correction factor $\beta_n$. It can be obtained from different method:

  (+) Fletcher-Reeves algorithm: $\beta_n^{FR}=\frac{\Delta x_n^T \Delta x_n}{\Delta x_{n-1}^T \Delta x_{n-1}}$. here multplication of $\Delta x_n^T$ and $\Delta x_n$, whcih is a square of steepest descent, gives a scalar and sum for all subsurface points.
  
  (+) Polak-Riebiere algorithm: $\beta_n^{PR}\frac{}{}$
  
  (+) Hestenes-Stiefel algorithm: $\beta_n^{HS}\frac{}{}$
  
  (+) Dai-Yuan algorithm: $\beta_n^{DY}\frac{}{}$  
 Popular choice $\beta_n = max{0, \beta_n^{PR}}$ which allows an automatic direction reset.  
  
  (+) Hager-Zhang algorithm:
  
(3) Update conjugate direction: $s_n = \Delta x_n + \beta_n s_{n-1}$. So here we are not simply using steepest descent direction $\Delta x_n$ but we are adding the additional term $\beta_n$ multiplied by previous search direction. At first iteration we use steepest descent direction, but all iterations greater than one, we can see that we are correcting the search direction using $\beta_n s_{n-1}$. Now if use the condition $\beta_n = max{0, \beta_n^{PR}}$, we can see that if $\beta$ becomes negative, which means zero we are only using steepest descent direction. It is refered to as automatic direction reset.

(4) Estimate step length $\mu_n$

(5) Update material parameters: $m_{n+1} = m_n + \mu_n s_n$ . Updateing the model but not along steepest descent direction but along the modified new search direction. 

This improves the convergence speed.

## Quasi-Newton Limited Memory Broyden Fletcher Goldfarb and Shanno (l-BFGS) Algorithm
The best optimisation method is the Newton method. The difference between the steepest descent and Newton method was that we multiply the gradient direction with the Hessian or inverse Hessian, i.e. the second derivative of the objective function w.r.t. different material aprameter combination. However the computation of this inverse Hessian is not easy. It requires a lot of memory (RAM) for large optimisation and often it is singular so we have to somehow stabilise it and overall it is computationally expensive to compute inverse Hessian.

To overcome this problem there is a quasi-Newtom method, it is called l-BFGS. The idea is to approximate the product of the inverse Hessian with gradient by fintie-differences.

### Quasi-Newton l-BFGS Method (loop-1)
At iteration step n:
(1) Compute the gradient $g_n = $
(2)
(3)
(4)

### Quasi-Newton l-BFGS Method (loop-2)
(1) Compute the Hessian $g_n = $

(2) Compute $z =$

(3) for i = n-m to n-1 do
      $\beta_i = \rho_i y_i^T z$ 
      
      $z = z+ s_i(\alpha_i - \beta_i)$
     end for
     
(4) H_n^{-1} g_n = z

(5) Update model $m_{n+1} = m_n - \mu_n H_n^-1 g_n$

There are other method like truncated newton method, which is better than quasi newton method.


# multi-modal objective function (multiple minima)



