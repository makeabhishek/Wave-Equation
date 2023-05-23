In this section we will discuss a little about the starting point of solving inverse problem and than get started with description of forward problem followed by inverse problem. Here, we will take a look of the linear and non-linear inverse problem.

## Motivation 
Objective of forward problem is to obtain the data $(d)$ from a known sub-surface structure or model $(m)$. Mathematically it can be repressented  in matrix form as 

$d=Gm$, 

where $(d)$ is the collected data, $(G)$ is a kind of 'Forward Mapping', and $(m)$ is the model property or material propert (such as velocity, elastic moduls, density, etc.). $(Gm)$ can be combinedly called forward problem. 

Solving a **forward probelem** is easy and straightforward for a known model parameers. However, finding the inverse of forward problem or determining the model parameters is a challenging task, beacuse inverse problems are illposed, i.e. problem with non-unique solution or non-exixting solution and unstable solution. 

In equation $d=Gm$, $(G)$ is oten has the dimension of parameters versus the number of data we collect in the experiment and thus $(G)$ is typically not a square matrix $(p \times q)$. Therefore, we cannot invert it. Recall, the condition to find inverse of a matrix is that it must be square. In summary, **$(G)$ is a non-square matrix and can not be invert.** We have to use other ways to find the inverse of a matrix. So the way we can think aout inverting the matrix is the **solution of least-squares problem**, which is discussed below.

## History
Before diving in to inverse problem, lets take a look of some historical advance in solving inverse problem. 
<!--
[//]: ![](Images/hadamard.JPG width=300)
-->

<img src="Images/hadamard.JPG" alt="fishy" class="bg-primary" width="200px" name="The caption for my image">
**

## Forward Problem
$d=Gm$, 

## Inverse Problem
Our objective is to find a model $m$ which is capable of reproducing our observable data $d$. However, in practice, it is impossible to find a $m$ that solve exactly $g(m)=d$. As an alternative, one can minimize the data residuals (measure of the misfit) to some tolerance $\delta$:

$r = d - g(m)$

Now the question is how can one measure the goodness of mistif which is the least. Therefore, we generally use the $L\_p$ norm to quantify the misfit:

$||r||\_p = (\sum_{i=1} ^{m} |r|^p)^\frac{1}{p} \leq \delta \sum_{k=1}^n$

### Linear inverse-problem

### Non-Linear inverse-problem

#### Gauss-Newton

##### Jacobian Computation
The cost of is mainly associated with the computation of the Jacobian. There are several ways to compute the Jacobian: 
  
  (#) Analytical expression. \
  (#) Finite-differences. \
  (#) Adjoint state methods (Plessix, 2006). \
  (#) Mesh adaptation. (Rucker et al., 2006) \
  (#) Approximation or compression of J (Broyden, 1965; Li et al., 2003) \
  (#) GPU computation (Borsic et al., 2012)

#### Levenberg-Marquardt method
