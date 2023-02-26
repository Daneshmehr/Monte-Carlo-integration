from math import exp
import numpy as np
from sympy import Symbol, integrate, exp, oo

# function for the trapezoidal rule
def TrapezoidalRule(a,b,f,n):
   h = (b-a)/float(n)
   s = 0
   x = a
   for i in range(1,n,1):
       x = x+h
       s = s+ f(x)
   s = 0.5*(f(a)+f(b)) +s
   return h*s

# function for the Gaussian quadrature with Laguerre polynomials
def GaussLaguerreRule(n):
   s = 0
   xgauleg, wgauleg = np.polynomial.laguerre.laggauss(n)
   for i in range(1,n,1):
       s = s+ xgauleg[i]*xgauleg[i]*wgauleg[i]
   return s

#  function to compute
def function(x):
    return x*x*exp(-x)


# Integration limits for the Trapezoidal rule
a = 0.0; b = 10000.0
# define x as a symbol to be used by sympy
x = Symbol('x')
# find result from sympy
exact = integrate(function(x), (x, a, oo))
# set up the arrays for plotting the relative error
n = np.zeros(40); Trapez = np.zeros(4); LagGauss = np.zeros(4);
# find the relative error as function of integration points
for i in range(1, 3, 1):
    npts = 10**i
    n[i] = npts
    Trapez[i] = abs((TrapezoidalRule(a,b,function,npts)-exact)/exact)
    LagGauss[i] = abs((GaussLaguerreRule(npts)-exact)/exact)
print ("Integration points=", n[1], n[2])
print ("Trapezoidal relative error=", Trapez[1], Trapez[2])
print ("LagGuass relative error=", LagGauss[1], LagGauss[2])
