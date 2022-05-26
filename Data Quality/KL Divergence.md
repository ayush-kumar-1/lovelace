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
Where $X = (x_1, \dots, x_n)$ and is a sample from an u