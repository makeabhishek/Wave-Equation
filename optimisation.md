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
