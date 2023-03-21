# Full-waveform inversion
Waveform-inversion is an optimisation procedure, where we try to fit the data and compare observed (experimental or field) and synthetic data (simulated or modelled) to image the internal structure of the object. Data can be fit using a quantitative measure of goodness between observations and synthetics. The inverse problem can be formulated in the form of misfit function (or error function) and the aim is to minimize the error or misfit, using numerical optimisation technique. A common choise of misfit function is 

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
