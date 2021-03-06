# 1. Introduction 
Current cyberbullying literature suffers from a sparsity of a high quality data. Effectively scaling up dataset sizes is key to leveraging the capabilities of large language models. Current dataset expansion approaches include scaling up annotations, dynamic query expansion, and synthetic data augmentation approaches. Each have their own merits and drawbacks. Manual annotations are expensive to scale, and are still prone to annotator bias and mislabeling. Dynamic query expansion suffers from low dataset diversity, inclusion of spam, and potential mislabeling of tweets from adjacent topics. Synthetic data augmentation approaches exhibit a tradeoff between computational complexity and example quality. We take a data-centric approach to expand dataset sizes while minimizing mislabeling, leveraging tweet metadata, and improving dataset quality. 

The twitter landscape is also rapidly changing with semantic meanings shifting with cultural waves. This poses potential for data drift. Either stationary assumptions must be carefully assessed, or tweets must be taken from a relatively short period in time (2-3 months) to ensure semantic stability. 

Tweets should take into account their metadata, this includes any retweets, number of followers/following for the account, quote tweets etc. This data must all be embedded into a single vector for classification, and poses some extremely difficult challenges of combining text data with numerical values, and graph representation of a tweet and potential retweets. I don't know how to solve this problem yet, but leveraging rich embeddings of tweets will utilize greater amounts of information and provide more robust (and potentially more accurate) predictions of cyberbullying. 



