# Characteristic Stability Index (CSI)
Characteristic Stability Index has the same formula as [[Population Stability Index]], but is performed on the features. Based on this we can conduct the same hypothesis test to determine if two populations are statistically different. We will generate CSI for every single input variable in a dataset. If we have tabular data with 95 independent variables, we will end up with 95 different CSI's - one for each independent variable. While PSI measures is a single measure for response variable shift, CSI is a flawed measure for a few particular reasons. 

1. Independence Assumption 

Assuming independence is difficult, and data drift may impact the independence of variables. Even datasets with low multicollinearity may suffer from endogeneity, confounding factors, or macroeconomic events. The solution is to consider the joint distribution of multiple variables, but this brings us to our second problem. 

2. Binning Explodes Support for Joint Distributions 

There are two ways to find a probability distribution for a variable in order to calculate KL Divergence, PSI, or CSI for a continuous variable. The first is to fit a continuous probability distribution either by hand, or by using some kind of kernel density estimation. Both of these processes are labor intensive, and difficult to replicate as scale. The solution is binning the data into $B$ buckets. This is a solid approach for a single variable, but for joint distributions this explodes the support of the distributions. If we divide 3 features into $B$ buckets our calculation explodes to $B^3$  bins to calculate over. It is likely that these bins will be sparse, leading to unstable behavior unless there is sufficient data. This makes a single CSI measure over the joint probability distribution of the feature space infeasible. In essence CSI runs into the curse of dimensionality. 

A possible solution to this problem is 