# **Numerical Optimization by Prof. Shirish K. Shevade, IISc**

- [youtube playlist](https://www.youtube.com/playlist?list=PL6EA0722B99332589)
- [slides and transcript](https://nptel.ac.in/courses/nptel_download.php?subjectid=106108056)


I assume you know, gradient of f(x) = 0 and Hessian f''(x) < 0 at minimum point.
 
## 11. Line Search Tenchiques

1. What is the stopping condition?
2. How to find the step length at each iteration?
	- Exact Line Search
	- Inexact line search. Armijo-Goldstein, Armjio -Wolfe.

## 12. Global Convergence Theorem

1. What does the algorithm converge?
2. When there is difficulty in using Armijo-Wolfe or Armijo-Goldstein, use Backtracking with Armijo Conditions.
3. How to find descent direction? d = -Ag 
	- If A=1, then it is Steepest Descent Method.
	- Then, look at how it converges for circular, elliptical contours and for rosenbrock functions.
	- 
## 13. Steepest Descent Method
1. Convergence depends upon the condition number H.
	- For circular contours (1 iteration)
	- For elliptical takes more iterations.

## 14. Classical Netwon Method
1. If d = -H^(-1)g, it is the classical Netwon method. At each point, we replace the function locally with a convex quadratic function and solve it in one step. Then, we go to the next point.
2. In the case of SDM, we replace each point with a line (first-order Taylor series).
3. Provides smooth convergence, less sensitivity to start point compared to Steepest.
### Downsides
1. Requires O(n3) computational effort for every iteration
2. No guarantee that d is a descent direction
3. No guarantee that f (xk+1) < f (xk) (no line search)
4. Sensitive to initial point (for non-quadratic functions)





