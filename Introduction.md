# Inversion 
There are a lot of methods to obtain the velocity or  from . A fundamantal method to obtain velocity of the medium is first arrival travel time tomography.
However, the resolution of first arrival traveltime tomography is restricted by the size of the first Frenel zone. The first arraival traveltime 
tomography can only reconstruct the long wavelength parts of the subsurface models. It cannot reconstruct the small parts.
The reason behind this is that we only consider pick the first arrival travel time and put them in non-linear problem to obtian velocity model. 
However, we actually ignore all the other information obtain from reflection, refraction, phase and amplitude information. We are only using the 
traveltime information of the first arraival. That is why the resolution is not good. To improve the resolution, the best option would be to consider
the whole recorded waveform. So if we are considering all the information in the non-linear inversion process. It is called full-waveform inversion.

So the aim is to obtain high resolution velocity model from the recorded time-traces. To obtain the high resoltion image, we have to solve mainly three problems:
(1) What is an "optimal" model? In other words, what is the model that can explain the 
time traces very well. Can we define some criteria, which can define a model that can fits the data very well. Once we have the criteria, next question is
(2) How can we find the model? What kind of optimisation that we use inorder t find this model.
(3) Is this model unique or are other model existing, which coluld explan the data equallly well?


## (1) What is an "optimim" model?
Lets we have some observed or experimental data, then we assume a subsurface model and we compute the synthetic/modelled data set using any numerical method, for exmaple Finite difference, finite element oand so on,
So we have two data \
  (1). Observed or experimental or field data $(u_{obs})$: \
  (2). Synthetic or modelled data $(u_{mod})$: \
  (3). Data residue $(\delta u = u_{mod} - u_{obs})$: \
  
  <img width="401" alt="Screenshot 2023-04-16 at 12 15 37 AM" src="https://user-images.githubusercontent.com/47937684/232332519-34dd9af5-178d-43c6-ba50-f923d4827e1b.png">

  
So based on data residue, we can quantify how well our modellled data explain the field data. The problem with this method is that we have to visually inspect the residuals fro every 
source-receiver pair. Hoever, if can use a measure which can condense this daa residue in some quantitative numbers.
One way to measure data residues is called $L2-norm$ (Residual Energy) of the data residual.
So we are taking the square of all the data residue samples in data and sum them. In simple form it can be written as a scalar product. $\delta u$ ia a column vector and taking its transpose means it is a row vector.
and the product of $\delta u^T \delta u$ is a scalar. $E = \frac{1}{2}\delta u^T \delta u$
This is the way to condence down all the data residue into single number $E$.
If the data residue high that means the misfit between the data is also high and vice versa.

So the next step is to reduce the data misfit. Therefore to find the optimum model, we have to minimise the objective function (E), because once the objective function is minimised, the data residue will be minimised.
This means that we have find a model which explains the experimetnal data very well (once the misfit is reduced). \

So the final aim is to minimise the objective function so that the systhetic data resembels the experimental data. Now the question is how to minimize the objective function (E) and therefore find a subsurface model that can explain the field data? \

### How to find an optimum model. or minimize the objective function (E)? 
The above problme looks like an optimisation problem, It is a non-linear optimisation problem. How to approach and solve this problem. These problems are usually have very large parameter space so typically it has a dimesnion of thousands to millions. Analysisng the objective funtion in space of this huge dimention is bit complicated in this world of 3D. To understand the probelm lets restrict us to 2D in to parameter space and then evaluate the misfit fucntion in this 2D parameter sapce.

A lot of mathemticians have created a lot of test functions for numerical optimisation. The plots of associated fucntion and their minima is described in wikipidea https://en.wikipedia.org/wiki/Test_functions_for_optimization#:~:text=In%20applied%20mathematics%2C%20test%20functions,Robustness.
<img width="1403" alt="Screenshot 2023-04-17 at 10 43 33 PM" src="https://user-images.githubusercontent.com/47937684/232673557-6284670e-8333-4b2a-8e5e-224a155832b8.png">

Lets take a commonly used objecive function, known as _Rosenbrock fucntion_ also called 'banana function'. We take the 2D Rosenbrock function, \
$E = (1-x_1)^2 + 100(x_2 - x_1^2)^2$ \

**To remind that the aim is to optimize material parameters of the subsurface or undergraound, therefore subtitute:**
$x_1 \rightarrow P-wave velocity V_p$ \
$x_2 \rightarrow density \V_p$, so the resulting Rosenbrock function will be \
$E = (1-V_p)^2 + 100(\V_p - V_p^2)^2$ \
Keep in mind though that this is seophysical non-sense. With this objective function we just want to learn that how to estimate a subsurface model by minimising the objecive function. Because the form of the objective function is known, we know where the minimum of this objective function would be. By this we can also test out numerical optimisation problem.\
<img width="479" alt="Screenshot 2023-04-17 at 10 52 12 PM" src="https://user-images.githubusercontent.com/47937684/232674541-be371b1e-b757-4a6a-b93a-b3b23f5804d6.png">
In above image, we can see the part of the parameter space. (Again this is a geophysical non-sense). Lets assume we have one point in the subsurface, and here we have plotted the density vs P-wave velocity. So all the points in the image resembles different models of p-wave velocity and density. Now for all these models, we can calculate the synthetic data (by solving wave equation for each V_P and density) and estimate the objective function. This simly means that take the data residue between synthetic and observed data, square them and calculate the sum over all our squared data-residues, and than we can associate for each model in the misfit function as shwon in the image, i.e. Residual energy. The color in this plot resembles differents models with different objecive funtion values. So we can see that red colours are where data residues are very high and we dont want to use, because these do not represent our field data very well. However, yellow models have a very low data resideu and thereofere can explain our data very well.  So we are interested at the minimum residue. \
So in order to find this optimum model we have to miminise the objective function $E$. We can do it by simple start in the parameter space ($m_1$) which has some p-wave velocity and density as initial guess. The aim is to start from this model and reac to the subsurface model. \
(1) Start search with initial guess $m_1$ \
(2) Define a direction in which we want to walk inside the parameter space, whcih is defined by a vector $\delta m_1$, define the step length and then simply walk straight in the parameter space  until we reach model $m_2$.  So, mathematically update the model iteratively : $m_2 = m_1 + \mu_1 \delta m_1$, model is a vector becaue we have two parametes p-wave velocity and density. $\delta m_1$ denotes the direction and $\mu_1$ is the step length.  \
<img width="478" alt="Screenshot 2023-04-17 at 11 10 06 PM" src="https://user-images.githubusercontent.com/47937684/232676966-61c2a441-e1c2-4df9-948d-bfcb3edf4a83.png"> \
## Big question: Which Direction $\delta m_1$ should we walk/choose?
<img width="459" alt="Screenshot 2023-04-17 at 11 11 02 PM" src="https://user-images.githubusercontent.com/47937684/232677133-fb3208c0-d6d5-49e1-8c58-d87595cae49c.png">

there would be some directin which are favourable and some should be avaoided because we cannot react to the minimum after some iterations. \
**We can move in the gradient direction to reach to the minimum.**
The image shows the countour lines of the objective function. One idea would be to move in the sttepest descent direction of the objective funstion. So it is the negative gradient of the objective funtion w.r.t. two material parameters. So the intutive answer would be to walk along gradinet of the objective funetion. \\

## How to find optimum search direction
We simply take a look, how the objective function in the visicinity of our intial model changes when we add a small perturbation $\delta m_1$ in any direction. Now we are assuming that these perturbations are very small, we can expand this expression in to a Taylor series. So we can approximate this by the value of the objective function at our starting point $E m_1$ plus the linear term (\delta m_1) of the Taylor series expansion, i.e. $\delta m_1 \frac{\partial E}{\partial m}_1$ and the gradient of objecive function w.r.t. material parametes plus quadratic term. In the expression $\delta m_1$ is a vector so quadratic term is written in term of transpose multiplied by second derivative of objective function w.r.t. material parameters.\
$E(m_1 + \delta m_1) \approx E(m_1) + \delta m_1 \delta m_1 \frac{\partial E}{\partial m}_1 + \frac{1}{2}\delta m_1^T H_1 \delta m_1$ So this is a Taylor expension in multiple dimensions.\
with the **Hessian** $H_{ij} = \frac{\partial^2 E}{\partial m_i \partial m_j}$. \
Now, we have to find optimum search direction so, fisrt calculate the derivate of objective function w.r.t. search direction and set derivative equal to zero:\

$\frac{\partial E(m_1 +m_2)}{\partial \delta m_1} = 0 + \bigg( \frac{\partial E}{\partial m} \bigg)_1 + \frac{1}{2}*2*\delta m_1 H_1 =0$. This is a basic methodology to find minimum of a function. In this case it is objective funciton and the parameter that we want to minimise is the search direction $\delta m_1$. Rearranging the equationa and multiply both side by inverted Hessian, which leads to

$\delta m_1 = - H_1^{-1} (\frac{\partial E}{\partial m})_1$, where $(\frac{\partial E}{\partial m})_1$ denotes the gradient direction of the objective function and $H_1^{-1}$ is the inverse Hessian matrix. So finally $\delta m_1 $ is the optimum search direction according to taylor series expansion analysis. So the optimum search direction is what we almost guess. Our guess was tht it is a negative gradient of objective funtion w.r.t. material parameters and mathemativally it is shown. However, a better search direection would be if we multiply the steepest descent with inverse Hessian. And this approach is called **Newton method**. As we can see from the Newton method figure, that we are not walking along the negative gradient direction, we are also using a little bit of the slope of the fucntion, whcih is described by the Hessian. **Newton method** $m_{n+1} = m_n - \mu_n H_n^{-1} \bigg( \frac{partial E}{\partial m}_n$ \
<img width="487" alt="Screenshot 2023-04-17 at 11 38 49 PM" src="https://user-images.githubusercontent.com/47937684/232681402-a189da88-7364-4c95-b349-be00b2f1a834.png">

So this is a resonalble aporach to mimimise the objective function from a given point in the parameter space. Now the problem with this approach is that we can calculate the graidnt of obejctive function easitly with mathematial tricks but the computation of inverse Hessian is very expensive and often the inverse Hessian is singular and we 
have to stabilise it some how. Also the Hessian is very large. So what we do is to approximate inverse Hessian by a parameter called **Preconditioning operator**. \
 **Gradient method** $m_{n+1} = m_n - \mu_n P_n^{-1} \bigg( \frac{partial E}{\partial m}_n$ \. 
 So preconditioniing should emitate the action of the Hessian. If we set Preconditioning to one, this is called **steepest descent method**. One of the issues with the steepest descent method that it has slow convergence, because it slowly propagate in  the valley, as shown below. But we can spped up this process by appropriate preconditioning operator. 
 <img width="447" alt="Screenshot 2023-04-17 at 11 48 57 PM" src="https://user-images.githubusercontent.com/47937684/232683170-57209747-f9e8-470d-a721-9f0ab27e860a.png"> \
 So now we have found the numerical method from which, we can find the objective function and thereofore minimise our data residue and therefore obtain the susbsurface model. 
 
 ## Final quesiton: How to calculate the gradient ($\frac{\partial E}{\partial m}$) of Objective function w.r.t. material aprameter?
How to calculate the gradient of this Objective function w.r.t. given material aprameter for a specific forward problem? There are a lot of approach to fint the gradient of objective function and the most prominent approach is called **ajdoint state method**. There are different ways to calculate adjoint state gradient directions, for example Lagrance multipliers, frequency domain, origginally these gradients were determined by using perturbation theory, developed by trantola. \
  (+) Adjoint state gradient estimation using Lagrange multipliers [Plessix,2006] \
  (+) Adjoint state gradient estimation in frequency domain [Pratt et al./ 1998, Plessix 2006] \
  (+) Adjoint state gradient estimation using perturbation theory [Tarantola, 2005, Mora 1987, Plessix 2006]. \
  
Adjoint state method is a computationally chep method to calculate the gradient and this apraoch can be applied to other fields also. \
 
Unfortunatelly this Adjoint state method works for linear problem, however the real senarios are non-linear, so the adjoint state approach may not really work.\ 
  (+) Global optimisation method can be used in non-linear case to implement FWI.
 
 ## Lets consider 2D acosutic wave equation

