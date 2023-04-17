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

So the next step is to reduce the data misfit. Therefore to find the optimum model, we have to minimise the objective function (E), because once the objective function is minimised, the data residue willl be minimised.
This tells that we have a model which explains the experimetnal data very well. So now the question is how to minimize the objective function (E)? \

### How to find an optimum model. or minimize the objective function (E)? 

