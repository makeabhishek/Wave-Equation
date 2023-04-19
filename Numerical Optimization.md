# Introduction to optimization
Mathematical optimization is the process of obtaining the best solution to a given problem from a set of possible options, given its desired outcome and constraints. 
The best solution could be to minimise the problem or maximise the problem. For example, the lowest cost, the quickest runtime, the lowest environmental impact, maximum profit.

Lets define optimisation probelm mathematically, \
+ Let $f(\mathbf{x})$ be a scalar function of a vector of variables $$\mathbf{x} = \begin{pmatrix}x_1 \\ x_2 \\ \vdots \\ x_n \end{pmatrix} \in \mathbb{R}^n$. 
*Numerical Optimization* is the minimization or maximization of this function $f$ subject to constraints on $\mathbf{x}$. This $f$ is a scalar function of $\mathbf{x}$, also known as the *objective function* and the continuous components $x_i \in \mathbf{x}$ are called the *decision variables*.

+ The optimization problem is formulated in the following way:


\begin{align}
&\!\min_{\mathbf{x} \in \mathbb{R}^n}        &\qquad& f(\mathbf{x}) \\
&\text{subject to} &      & g_k(\mathbf{x}) \leq 0,\ k=1,2,..., m\\
&                  &      & h_k(\mathbf{x}) = 0,\ k=1,2,..., r\\
&                  &      & m,r < n. \label{eq:1}\tag{1}
\end{align}

+ Here, $g_k(\mathbf{x})$ and $h_k(\mathbf{x})$ are scalar functions too (like $f(\mathbf{x})$) and are called *constraint functions*. The constraint functions define some specific equations and/or inequalities that $\mathbf{x}$ should satisfy.


## A Solution
  
A *solution* of $f(\mathbf{x})$ is a point $\mathbf{x^*}$ which denotes the optimum vector that solves Eq.\eqref{eq:1}, corresponding to the optimum value $f(\mathbf{x^*})$.

In case of a *minimization* problem, the optimum vector $\mathbf{x^*}$ is referred to as the *global minimizer* of $f$, and $f$ attains the least possible value at $\mathbf{x^*}$. To design an algorithm that finds out the global minimizer for a function is quite difficult, as in most cases we do not have the idea of the overall shape of $f$. Mostly our knowledge is restricted to a local portion of $f$.

+ A point $\mathbf{x^*}$ is called a *global minimizer* of $f$ if $f(\mathbf{x^*}) \leq f(\mathbf{x}) \forall\ x$.

 
+ A point $\mathbf{x^*}$ is called a *local minimizer* of $f$ if there is a neighborhood $\mathcal{N}$ of $\mathbf{x^*}$ such that $f(\mathbf{x^*}) \leq f(\mathbf{x}) \forall\ x \in \mathcal{N}$.
