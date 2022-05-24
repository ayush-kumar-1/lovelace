# Population Stability Index
> Population Stability Index (PSI) compares the distribution of predicted probability in scoring data with predicted probability in training data. The idea is to check “How different the current scored data is, compared to the training data”.

$$PSI = \sum (\%Actual - \%Expected) \times \text{ln} \frac{\%Actual}{\%Expected}$$Population Stability Index essentially buckets a single column of data into discrete bucvkets