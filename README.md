# StVAR

Vector AutoRegression Statistical Model with Student's Distribution using Maximum Likelihood Estimation.

The primary goal of this package is to model the conditional mean and variance of several associated financial variables simultaneously and through time. That information can be utilized for risk measurement, portfolio optimization, option pricing, and prediction. The main assumption is that the stochastic process resembles a joint Student's t distribution and Markov process.
For a complete explanation please read the "StVAR Model Explanation.pdf"

## Installation
Run the following to install:

Download "StVAR-0.0.4.zip" file and unzip it in your computer,

In command prompt change the current directory to the location of unziped file. e.g. cd C:\Users\...\StVAR-0.0.4,

In comand prompt ''' pip install . ''',


## Usage
Please read StVAR model expalanation 

Import StVAR Package
```ruby
import StVAR as stv
```

Simulate 4 variables with student's t distribution, means are ordered in a list [5, -2, 0, 3], v is degree of freedom and n is number of observations
```ruby
sim = stv.Simulation_St([5, -2, 0, 3], 4, n=100, trend=False)  
data = sim
```

Plot the graphs 
```ruby
for i in range (data.shape[1]):
    fig, ax = plt.subplots(figsize=(20, 10))
    ax.plot(data.iloc[:,i], color='r')    
    plt.show()
```
    
Specifying degree of freedom, mean trend's degree, and number of lags
```ruby
v = int(input("Enter the dof: "))
trend = int(input("Enter the Mean trend's degree: "))
lag = int(input("Enter the number of lags: "))
```

StVAR MLE estimator, reparametrization, std.errors
```ruby
# StVAR MLE estimator, reparametrization, std.error,
a, se_a, A, se_A, Omega, se_Omega, Q, estimates, se_estimates, hess_inv, jac = stv.StVAR_est(data, v, trend, lag, scaled = True, cheby = False)
loglik, logliks, M, SIGMA = stv.St_VAR_likelihood(estimates, data, v, trend, lag, scaled = True, cheby = False, out=True, Mt_all=False)
```

Var Cov Estimation
```ruby
Var_Cov = stv.Var_Cov(data, v, trend, lag, Q, Omega, estimates, scaled = True, cheby = False)
```

Fits, and residuals
```ruby
Fit = stv.fit(data, v, trend, lag, a, A, Q, Omega, estimates, scaled = True, cheby = False)
Adj_Fit = stv.Adj_fit(data, v, trend, lag, a, A, Q, Omega, estimates, fit = Fit, scaled = True, cheby = False)
```

Mis-specification Testing
```ruby
stv.MS_testing(data, v, trend, lag, var_cov = Var_Cov, fit = Fit, adj_fit = Adj_Fit,  scaled = True, cheby = False)
```
