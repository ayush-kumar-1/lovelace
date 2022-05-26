# Kolmogorov-Smirnov Test
The KS-Test is built to detect the difference in distribution between two continuous distributions based on their CDF's. This can be two unknown samples (2-sample KS-Test) or a single unknown variable and a target distribution (i.e. normal, exponential, etc.) The KS test statistic can be calculated with 

$$D=\sup |P_1,n(x) - Q_2,m(x)|$$
The KS test statistic follows the Kolmogorov distribution.   
![[Pasted image 20220526141507.png]]
To conduct a KS test we can simply use the SciPy library. The KS test works at very low sample sizes, but is not the most powerful test for detecting normality. In the case of normal distributions procedures are to standardize the data and calculate the KS test statistic with the standard normal distribution. For large sample sizes errors may propagate, but downsampling or kernel approximation may be appropriate. KS test statistic is well defined for discrete random variables, but for discrete RV's with few levels the KL divergence may be a more appropriate measure. 