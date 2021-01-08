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

from StVAR import *

%simulate 4 variables with student's t distribution, means are ordered in a list [5, -2, 0, 3], v is degreefo freedom and n is number of observations

sim = Simulation_St([5, -2, 0, 3], 4, n=100, trend=False)  

