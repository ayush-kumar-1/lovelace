---
tags:
- dataquality
---
# Population Stability Index
[Statistical Properties of PSI](http://www.stat.wmich.edu/naranjo/PSI.pdf )
> Population Stability Index (PSI) compares the distribution of predicted probability in scoring data with predicted probability in training data. The idea is to check “How different the current scored data is, compared to the training data”.

$$PSI = \sum (\%Actual - \%Expected) \times \text{ln} \frac{\%Actual}{\%Expected}$$
## Hypothesis Testing for PSI
Population Stability Index essentially buckets a single column of data into discrete buckets (or uses the discrete values of a discrete probability distribution). Let $X = (X_1, X_2, \dots, X_B)$ be a random vectors with parameters $n$ and $p = (p_1, p_2, \dots, p_B)$ where $B$ is the number of buckets and $p_i >0$ and is the probability that $X = X_i$. We can define a new random vector $Y = (Y_1, \dots, Y_B)$ with parameters $m$ and $q$ analogous to $n$ and $p$. 
$$PSI = \sum_{i=1}^B (p_i - q_i) \text{ln}\frac{p_i}{q_i}$$
When $p_i = q_i$ the value $(\frac 1 n + \frac  1 m)^{-1} PSI \sim \chi^2_{B-1}$. From this we can conduct the following hypothesis test to determine if there has been statistically significant drift. 

$$H_0: P = Q \quad H_a: P \neq Q$$
We reject if 
$$PSI > \left(\frac 1 n + \frac 1 m\right) \chi^2_{\alpha, B-1}$$
## Drawbacks 
There are some notable drawbacks of PSI. 
	1. There may not be available data streams to measure PSI, at time of prediction - data may not get labeled for some time after prediction, or may never be labeled. This presents an inherent problem with PSI because it may create delays in detection of 