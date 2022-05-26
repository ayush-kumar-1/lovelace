---
tags: 
- dataquality
---
# Kullback-Leibler Divergence 
Wikipedia definitions: [[Kullback–Leibler divergence - Wikipedia]]

KL Divergence is a measure of distance between two probability distributions. It also known as #relativeentropy. The formula for KL divergence is as follows in the discrete case. 

 $$D_{\text{KL}}(P\parallel Q)=\sum _{x\in {\mathcal {X}}}P(x)\log \left({\frac {P(x)}{Q(x)}}\right)$$
 In the continuous case we simply model this utilizing an integral. An important characteristic of KL divergence is that it is not symmetric. In general this means that
$$D_{\text{KL}}(P||Q) \neq D_{\text{KL}}(Q||P)$$
We can consider the symmetrical version as 
$$D_{\text{KL}}(P||Q) + D_{\text{KL}}(Q||P)$$
$$\sum _{x\in {\mathcal {X}}}P(x)\log \left({\frac {P(x)}{Q(x)}}\right) + \sum _{x\in {\mathcal {X}}}Q(x)\log \left({\frac {Q(x)}{P(x)}}\right)$$
$$\sum _{x\in {\mathcal {X}}}P(x)\log \left({\frac {P(x)}{Q(x)}}\right) - Q(x)\log \left({\frac {P(x)}{Q(x)}}\right) = \sum _{x\in {\mathcal {X}}} (P(x)-Q(x)) \log \frac {P(x)}{Q(x)}$$
This symmetrized version is exactly the [[Population Stability Index]]. 

## Continuous Implementation of KL Divergence 
For two unknown continuous distributions, the KL divergence is not well defined and I don't recommend using it. If approximate probability distributions can be calculated and fitted then it may be worth pursuing through numerical close form solutions. If needed there is a decent algorithm for approximation using empirical CDFs described in [Kullback-Leibler divergence estimation of continuous distributions](https://www.tsc.uc3m.es/~fernando/bare_conf3.pdf). 

I'll describe the algorithm and give the python implementation here. First we find the empirical CDF of a distribution function as 

$$P_e(x) = \frac 1 n \sum_{i=0}^nU(x-x_i)$$
Where $X = (x_1, \dots, x_n)$ and is a sorted sample from an unknown distribution, and $U$ is the unit-step function. In python we implement this as 
```python 
def empirical_cdf(data: np.ndarray, x: float): 
    """
    Finds the emprical cdf function from a given distribution. 
    """
    summed = (data < x).sum()
    if summed == 0: 
        return 0
    
    return (data < x).sum()/len(data)
```
Next we define a continuous piece-wise linear extension this function. 
$$P_c(x) 
\begin{cases}
0, & x < x_0 \\
a_ix + b_i, & x_{i-1} < x<x_i\\
1, & x_{n+1} \leq x
\end{cases}$$
We can define the middle values as linear interpolations of the nearest values. This is not the most efficient implementation because repeatedly running over the entire array adds up to $O(n)$ , a smarter implementation using binary search and leveraging the already sorted `data` array would greatly improve efficiency. 
```python
def smoothed_empirical_cdf(data: np.ndarray, x:float): 
    """
    If x is in data returns the empirical cdf. If x is not 
    in the data returns a linear approximation based on the 
    2 nearest neighbors. 
    """
    if x in data: 
        return empirical_cdf(data, x)
    
    if x > np.max(data): 
        return 1 
    
    if x < np.min(data): 
        return 0
    
    x_0 = np.min(data[data > x])
    x_1 = np.max(data[data < x])
    
    y_0, y_1 = empirical_cdf(data, x_0), empirical_cdf(data, x_1)
    
    return y_0*(x_1 - x)/(x_1 - x_0) + y_1 * (x-x_0)/(x_1-x_0)
```

Once we have the empirical CDF we can define our estimator as 
$$\hat D(P||Q) = \frac 1 n \sum_{i=1}^n\log\frac{\delta P_c(x_i)}{\delta Q_c(x_i)}$$
where $Q_c$ is the stepwise approximation of the empirical CDF for the distribution to be compared. 

