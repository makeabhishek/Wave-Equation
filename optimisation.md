Optimization technique (OT) or Mathematical optimization or mathematical programming is a powerful set of tools to maximize or minimse an objective of a problem. There are 

OT aims to slelect a best element, with respect to some criterion, from some set of available alternatives. Generally, it is divided into two subfields:
(i) Discrete optimization and 
(ii) continuous optimization. 

## How did we determine the minimum of a function in school days?
To find the minimum of a function in our school days we use to perform differentiation of a function i.e., find the gradient of a function and equate it to zero. 
We normally didn’t apply gradient descent. So why we to use other methods, such as iterative techniques while solving the problems in computers? 

## How to determine Maxima and Minima of a function?
### Plotting the fucntion
  + The first way is by using a graph. You can find the Maxima and Minima value visually by graphing or plotting the equation and finding the value on the graph. But it gets complicated when the fucntion is complex.
### Using Derivatives
  In a smoothly changing function a maximum or minimum is always where the function flattens out (except for a saddle point).
  + ![fucntion](https://user-images.githubusercontent.com/47937684/230793829-1015b391-22a0-49b2-8ce5-b8d5a45c5ab1.svg)
  + Where does it flatten out:  Where the slope is zero. 
  + Where is the slope zero?  The Derivative tells us!
  + Example: $h = 3 + 14t - 5t^2$, find the maximum of this function. Using derivatives we can find the slope of that function: \
  $dy/dx = 14 - 10x$, now find when the slope is zero, so equate the derivative equal to zero. $14 - 10x=0; x = 1.4$
  The slope is zero at t = 1.4, and 'h' at this point is h = 3 + 14×1.4 − 5×1.4^2; h= 12.8
  + "Second Derivative: less than 0 is a maximum, greater than 0 is a minimum"
  
## Why to use gradient descent to optimize our models?

From a mathematical perspective, it seems odd. 
Gradient descent relies on knowledge of the gradient to ‘slide down the slope’, but  Instead, we just find the minimum analytically by directly solving 
for when the gradient is 0. So why then, when we move to the domain of computers, do we suddenly switch tactics and use iterative techniques? Also, 
why do we use gradient descent instead of, for example, Newton descent, the other popular iterative optimization technique?

### What is gradient of function ($\nabla$)
If a function is defined as $f(x\_1,x\_2)=x\_1^2 + x\_2^2$, what will be its gradient $\nabla f = ?$. Before jumping into gradient lets see the **derivatives** of a function. Lets assume a function $f(x) = x^2$, where $x$ is a scalar. This is a quadratic function which is like a parabolic curve if we plot it. If we take the derivative of this function w.r.t. $x$. In the figure $x$ is represented by $\theta$ \
$f'(x)=\frac{df(x)}{dx}=2x$. The derivative or slope of $f(x)$, whcih is a straight line, is zero at $x=0$, it is positive for $x>0$ and negative for $x<0$.

![x2](https://github.com/makeabhishek/Wave-Equation/assets/47937684/3c97c148-3178-4d3b-abe2-9879cb405039)

Now we take a look of Gradient: Gradient captures all partial derivatives of a multivariable function. In above derivatives we talk about a fucntion which has only one scalar variable. Now we have two variable, $x\_1$ and $x\_2$. i.e., $X= [x\_1 x\_2]^T$, column vector. Fint the inner product 
$f(x)=X^TX = [x\_1 x\_2]^T [x\_1 x\_2]^T$, where the dimension of $f(x)$ will be 1x2 and 2x1, so if we do the multiplication we will get $x\_1^2 + x\_2^2$. So in some sense this function  square each element of multivariable fiucntion and sum together. 

As we have two variables, we have to find partial derivative as we have multi-variable funciton. So we have a function $X = x\_1^2 + x\_2^2$ Then partial derivative w.r.t. $x\_1$ and $x\_2$. $\frac{\partial f}{\partial x\_1}=2x\_1$ and $\frac{\partial f}{\partial x\_2}=2x\_2$ 

To find the gradient $\nabla f$, we need to put all the partial derivatives together. As the funciton $f(x\_1,x\_2)$ has two varaibles, gradient will also have two partail derivatives. $\nabla f = [\frac{\partial f}{\partial x\_1} \quad  \frac{\partial f}{\partial x\_2}]^T$ $=$ $\nabla f = [2x\_1 2x\_2]^T = 2[x\_1 x\_2]^T= 2X$. It measn that the gradient is simple $2X$. \

**Why gradient is useful?** In above case for a function $f(x)=X$, whcih has two variable, its gradeint is simply $2X$, so it is easy to extend this concept to n dimentional variable problem. Lets take a more complex function. $f(x)=(x\_1 + 2x\_2^3)^2$. Using the chain rule
$\frac{\partial f}{\partial x\_1} = 2(x\_1 + 2x\_2^3) \frac{\partial}{\partial x\_1}(x\_1 + 2x\_2^3) = 2(x\_1 + 2x\_2^3)^2$ 

$\frac{\partial f}{\partial x\_2} = 2(x\_1 + 2x\_2^3) \frac{\partial}{\partial x\_2}(x\_1 + 2x\_2^3) = 12x\_2^2(x\_1 + 2x\_2^3)$ 

$\nabla f = [2(x\_1 + 2x\_2^3)^2 \quad  12x\_2^2(x\_1 + 2x\_2^3)]^T$

### Array, Norm, and Dot Product with NumPy

In numPy it is important understand the 1D and 2D array.

**Norm/length of array or vector**: norm of vector can be obtained by sqaring each element of vector than sum and take the squareroot of them, $||X||=\sqrt(\sum\_{i=1}{^n} x\_i^2)$. For example if $X=[3 \quad 4] \rightarrow ||X||=\sqrt{3^2 + 4^2} = 5$. In python we can find norm from numpy package in linear algebra "numpy.linalg.norm(X)"

**Dot product or inner product**: it can be defined for 1D array of same length. Dot product of array is always scalar. For exaple $<x,y> = \sum_{i=1}^n x\_i y\_i$. In numpy we can use numpy.dot(x,y). If both x and y are 1-D arrays, it is inner product of vectors (without complex conjugate). However of x and y are 2D arrays, it is matrix multiplication, but using 'matmul' of x and y is preffered  or else reshape the 2D array to 1D to ficd dot product.

**Matrix Multiplication**:
matrix multiplication of $m \times n$ and $n \times 1$ array, we will get $m \times 1$ matrix. For matrix multiplication in python it should be 2D array, so even a 1D array need to have dimention of $n \times 1$. In python 'np.matmul(A,b)' is used. for multiple arrays np.linalg.multi_dot([A,B,C,D]) can be used.

**Matrix Inverse** Consider a square matrix $A \in R^{n \times n}$ and  $B \in R^{n \times n}$ have the property that $AB=BA=I\_n$. B is called the inverse of A and denoted by $A^{-1}$. In numpy we can use 'B=np.linalg.inv(A)'. If we multiply A and B it should give identity matrix. So we can do 'np.matmul(A,B)'.

**Does the Inverse exist?** Compute the determinant: when the determinant of a square matrix is zero (Singular matrix), the inverse does not exist. In Python we can find determinant by 'np.linalg.det(A)'

**Matrix transpose** In python we can do transpose by 'A.transpose or A.T'

**Pseudo Inverse :**  The easieset way to understand pseudo inverse is to look the linear equation \
$A \theta = b$ Multiply both side by $A^T$ $A^T A \theta = A^Tb$ Now multiple $(A^T A)^{-1}$ both side we get, $\theta =(A^T A)^{-1} A^T b$ i.e., $\theta =pseudo_inverse(A) *b$In Python we can find pseudo inverse by using 'B=np.linalg.pinv(A)'

**Vector Norm:** 
A vector is a 1D array. Informal defieition of norm is that the "norm": measure the size of vector. The formal defienition of norm is that the norm of a vector is a function that maps a vector to a positive value. 

