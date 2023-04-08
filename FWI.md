# Full-waveform inversion
Few Points to get an essense of the FWI
  + The gradient of the FWI objective function is required to find the optimal solution (step for a optimisation problem); \
  + 


Waveform-inversion is an optimisation procedure, where we try to fit the data and compare observed (experimental or field) and synthetic data (simulated or modelled) to image the internal structure of the object. Data can be fit using a quantitative measure of goodness between observations and synthetics. The inverse problem can be formulated in the form of misfit function (or error function) and the aim is to minimize the error or misfit, using numerical optimisation technique.  The choice of waveform misfit is an important part of inversion and optimisation, and there are multiple options available
[e.g. Tromp et al., 2005, Fichtner et al., 2008, Bozdag et al., 2011]. We can define an objective function $[\chi(m)]$, where $\chi$ can represent any waveform misfit function. As required to minimise the objective function, each iteration requires computing the gradient of misfit function $\chi$ with respect to the model parameters $m$, which, using the chain rule, can be written as

$$ \frac{\partial \chi}{\partial m_i} = {\frac{\partial \chi}{\partial u}}^T \frac{\partial u}{\partial m_i} $$

The problem which becomes apparent in Eq. (2) is that the computation of $\frac{\partial u}{\partial m_i}$ would require solving Eq. (1) once for
each model parameter $m_i$, with i = 1, 2, . . . , M, in order to compute a finite-difference type gradient. This becomes practically impossible quickly as the number of model parameters increases, making any realistic FWI problem unsolvable in practice. Adjoint-state method is the other way to solve this problem.

A common choise of misfit function $[\chi(m)]$ is 

$$ \chi(m) = \frac{1}{2} \sum_{i=1}^N \int \bigg|F([s_i(m;t)] - F[d_i(m;t)]\bigg|^2 dt + \alpha_kH_k^{-1} R[-g_k]$$ 

where 
  + $s$ and $d$ are synthetic and observed data, 
  + $F$ is a data processing operator (also called called _**pre-processing**_ operator), and the sum is taken over the sources and receivers (i=1 ... N). Observed and synthetic data typically require some kind of signal processing to make meaniingful comparison. Bandpass filter is often used for $F$ operator. Sometimes additional sprocessing are required such as normalization, muting, denoising, or redatuming.
  + $\alpha$ is step length detemined by line search, 
  + $H$ is the Hessian matrix of second order derivatives of $\chi(m)$.
  + $R$ is regularisation, smoothing, or image processing operator, whciih is also referred as _**post-processing**_ operator. 

Data fit (or error) between observed and synthetic data is improved by iteratively updating the model by using non-linear optimiszation algorithm to the misfit function $\chi(m)$. A new model is generated with each iteration:

$$m_{k+1} = m_k + \alpha_kH_k^{-1} R[-g_k]$$

## Part 0: Observed/experimental data collection

## Part 1: Forward modeling[Ref](https://wiki.seg.org/wiki/Full-waveform_inversion,_Part_1:_Forward_modeling "text title")


## Part 2: Adjoint modeling


## Part 3: Optimization

### Non-linear optimisation methods



References:
[1] Thrastarson, Solvi, Dirk-Philip van Herwaarden, and Andreas Fichtner. "Inversionson: fully automated seismic waveform inversions." (2021).
[2]
[3]
