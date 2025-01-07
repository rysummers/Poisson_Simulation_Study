# Simulation Study on Poisson Regression: Type I and Type II Error Rates

This repository contains code and results for a simulation study examining the performance of Poisson regression models under violations of the equi-dispersion assumption (mean = variance). Specifically, it evaluates the Type I (false positive) and Type II (false negative) error rates when analyzing count data that are over-dispersed or under-dispersed.  

## Objectives  

The primary goals of this simulation study are:  

1. **Assess Type I Errors**: Evaluate how often Poisson regression incorrectly identifies significant differences between two groups when no true differences exist, especially when the variance differs from the mean.  
2. **Assess Type II Errors**: Measure the ability of Poisson regression to detect true differences between groups across varying effect sizes and variance-to-mean ratios.  

## Background  

Poisson regression is commonly used to model count data in public health and medical research. However, its strict assumption that the mean equals the variance often does not hold in real-world datasets.  

- **Over-dispersion** occurs when the variance exceeds the mean, leading to inflated Type I error rates.  
- **Under-dispersion** occurs when the variance is less than the mean, increasing Type II error rates.  

This study explores how these violations impact the reliability of Poisson regression and provides insights into alternative modeling approaches.  

## Methods  

Simulations were conducted using the following steps:  

1. **Data Generation**: Count data was generated using the Poisson distribution (`rpois()` in R), with modifications to simulate over-dispersion and under-dispersion.  
2. **Variance Manipulation**: Variance-to-mean ratios were adjusted to range from 0.1 to 10 using a scaling parameter.  
3. **Modeling**: A generalized linear model (GLM) with the Poisson family was applied to compare two groups.  
4. **Error Calculation**:  
   - **Type I Errors**: Simulations where the two groups had no true difference in their underlying distributions.  
   - **Type II Errors**: Simulations where the two groups differed by varying effect sizes (Cohen’s d: 0.1 to 1).  
5. **Repetition**: Each simulation scenario was repeated 10,000 times for five sample sizes (10, 25, 50, 75, 100).  

All analyses were conducted in R v4.4.1 (“Race for Your Life”).  

## Repository Contents  

This repository contains the following files and directories:  

- **`Code`**:  
  - `Pois_Regr_Sim.RMD`: RMD file for simulating Type I and Type II error rates. The code is organized into code chunks to follow the format of the final report. 
- **`Data`**:  
  - The simulation was computationally expensive due to testing various Cohen's d effect sizes and degrees of dispersion. To facilitate easy code execution without running the actual simulation, I exported the results to two CSV files. However, to fully reproduce my results, running the complete simulation on a high-performance computer is recommended.
    - type1_results.csv
    - type2_results3.csv
- **`Results`**:  
  - Tables and visualizations of Type I and Type II error rates.  
- **`Plots`**:  
  - Graphical outputs showing error rates across variance-to-mean ratios and effect sizes.  
 

## Results  

Key findings include:  

- **Type I Errors**: Over-dispersion significantly inflates false-positive rates (e.g., from 5% to ~15% when the variance-to-mean ratio doubles). Under-dispersion decreases false-positive rates linearly.  
- **Type II Errors**: Robust to dispersion violations, with errors primarily influenced by sample size and effect size rather than dispersion.  
- **Recommendation**: Use alternative models, like negative binomial or quasi-Poisson, for over-dispersed data to mitigate inflated Type I error rates.  


## Acknowledgments  

This work contributes to improving statistical methods in public health and medicine by addressing challenges in count data analysis.  

## License  

This project is licensed under the MIT License. See `LICENSE` for details.  
