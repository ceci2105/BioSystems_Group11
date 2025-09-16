# Setup & Imports
We take the working SIRD model code from the practical and use it as a backbone of all further calculations.

# Part 1: Parameter Analysis Function
The function uses the SIRD model and tests the simulation outcome of 5, hardcoded, recovery rates values as specifiied in the instructions. For each recovery rate it creates a subplot showing its epidemic curves: Evolution of the number of Suscebtible, Infected, Recovered & Dead among the simulation population. Furthermore, for each recovery rate It also creates a record in the 'results' dataframe, which stores the following information: ['gamma', 'R0', 'peak_infected', 'peak_day', 'total_deaths'].

After running all 5 scenarios the functions dispplays the final visualization of all 5 epidemic curves and outputs the result dataframe. We then print the result dataframe and also visualize its findings, showing how each of the result data columns changes with respect to recovery rate (gamma).

# Part 2: Scenario Comparison
In this part we extend the SIRD model analysis to compare two different scenarios with varying transmission and mortality rates:

- High Transmission: β = 0.4, μ = 0.02  
- Low Transmission: β = 0.2, μ = 0.005  

For both scenarios, the simulation is run across the same set of recovery rates (γ) and the results of each run are stored in the 'results' dataframe, including the same metrics as in part 1: ['gamma', 'R0', 'peak_infected', 'peak_day', 'total_deaths'].
An additional column 'scenario` is added to distinguish between the two cases.

The outcomes are then visualized in a set of comparative plots that show how each metric changes with the recovery rate, allowing a direct comparison of High vs Low 
Transmission scenarios.

From the results we can see that the High Transmission scenario leads to higher $R_0$, a larger and earlier infection peak, and more total deaths, 
making it significantly worse for public health. The Low Transmission scenario shows smaller peaks and fewer deaths, highlighting the importance of reducing 
transmission rates.

# Part 3: Policy Recommendations


# Conclusions
