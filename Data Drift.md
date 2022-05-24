# Data Drift
Data drift is unexpected and undocumented changes to data structure, semantics, and infrastructure that is a result of modern data architectures. Data drift breaks processes and corrupts data, but can also reveal new opportunities for data use.

Oftentimes the distribution of data at time of training becomes obsolete by the time production is ready for data. As we stream new data checking for changes in the distribution of data is key to preventing performance failures in your machine learning pipeline. 

## Statistical Tests for Data Drift 
- [[Kullback–Leibler divergence - Wikipedia]]
- [[Population Stability Index]]
- [[Characteristic Stability Index]]

## What is Data Drift? 
In supervised and semi-supervised settings we assume that the each pair of observations $(x, y)$ are drawn independently from the same joint distribution $p(x,y)$. As our data begins to diverge from this distribution we arrive in a scenario where our key model assumptions do not hold. Ensuring b