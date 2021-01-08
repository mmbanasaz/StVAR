# StVAR

Vector AutoRegression Statistical Model with Student's Distribution using Maximum Likelihood Estimation.

The primary goal of this package is to model Mean and Variance of several associated financial variables simultaneously and through time. The main assumption is that their stochastic behavior resembles Student's t distribution.  
For a complete explanation please read the "StVAR Model Explanation.pdf"

## Installation
Run the following to install:

Download "StVAR-0.0.1.tar.gz" file and unzip it in your computer,

in command prompt change the current directory to the location of unziped file. e.g. cd C:\Users\...\StVAR-0.0.1,

in comand prompt ''' pip install . ''',


## Usage
Please read StVAR model expalanation 

import StVAR Package
```ruby
from StVAR import *
```

simulate 4 variables with student's t distribution, means are ordered in a list [5, -2, 0, 3], v is degree of freedom and n is number of observations
```ruby
sim = Simulation_St([5, -2, 0, 3], 4, n=100, trend=False)  
data = sim
```

plot the graphs 
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
a, se_a, A, se_A, Omega, se_Omega, Q, estimates, hess_inv, jac = StVAR_est(data, v, trend, lag)
```

Var Cov Estimation
```ruby
Var_Cov (data, v, trend, lag)
```

fits, and residuals
```ruby
fit(data, v, trend, lag)
St = Adj_fit(data, v, trend, lag)
```

Mis-specification Testing
```ruby
MS_testing(data, v, trend, lag)
```
