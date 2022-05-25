# Data Drift
Data drift is unexpected and undocumented changes to data structure, semantics, and infrastructure that is a result of modern data architectures. Data drift breaks processes and corrupts data, but can also reveal new opportunities for data use.

Oftentimes the distribution of data at time of training becomes obsolete by the time production is ready for data. As we stream new data checking for changes in the distribution of data is key to preventing performance failures in your machine learning pipeline. 

## Statistical Tests for Data Drift 
- [[KL Divergence]]
- [[Population Stability Index]]
- [[Characteristic Stability Index]]

These are all related to one another, see [[KL Divergence]] for more details. I highly recommend using the PSI because of its known distribution at sufficiently large sample sized, due to the central limit theorem. 

## What is Data Drift? 
In supervised and semi-supervised settings we assume that the each pair of observations $(x, y)$ are drawn independently from the same joint distribution $p(x,y)$. As our data begins to diverge from this distribution we arrive in a scenario where our key model assumptions do not hold. Ensuring proper data quality means making sure our data satisfies the assumptions of our model. Model assumptions can vary widely, data can range from images, text, tabular, to complicated graph structures. Detecting drift can become a complicated problem that should be addressed before the first model is built. 

Formally we have data drift when the training distribution $T$ and the real world distribution $R$ diverge.
$$P(x_t, y_t) \neq P(x_r, y_r)$$
Not only can data drift mess with overall distribution, it can also violate assumptions of independence if there are external factors changing the distribution, or we see drift in a particular direction due to macroeconomic conditions. Some causes of drift to watch out for include: 
1. Sample selection bias 
2. Non-stationary environment 

### Feature Drift 
Feature drift occurs when the underlying distribution of our feature vector changes, but the ground truth relationship between $x$ and $y$ remains the same. In simpler terms we more frequently observe data that previously was under represented, or not present. 

Formally feature drift (or covariate drift) occurs when 

$$P(x_t) \neq P(x_r) \text{ and } P(y_t|x_t) = P(y_r|x_r)$$
![[Example of Feature Drift.png]]
Image from [Dataset Shift in Machine Learning | The MIT Press](https://mitpress.mit.edu/books/dataset-shift-machine-learning)

### Concept Drift 
This is the opposite of feature drift. Our feature/covariate distributions remain the same, but our targets have changed. Formally concept drift occurs when
$$P(x_t) = P(x_r) \text{ and } P(y_t|x_t) \neq P(y_r|x_r)$$
### Dual Drift
As you may have guessed by this point dual drift is when we have both feature drift and concept drift at the same time. 
$$P(x_t) \neq P(x_r) \text{ and } P(y_t|x_t) \neq P(y_r|x_r)$$
