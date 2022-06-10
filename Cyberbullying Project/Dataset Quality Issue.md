# Dataset Quality 
Cyberbully detection suffers from many dataset quality issues, the largest of which has traditionally been class imbalance. This problem is exacerbated when discussing the fine-grained problem. Wang et. al tried to address this problem by using a dynamic query expansion procedure, but upon close inspection this may only be a piecemeal solution due to lack of data diversity. Lack of diversity may led to detection systems that are not robust. Based on the Table 1 in Wang et. al the classes most prone to this lack of diversity may be age, ethnicity, and religion. A first step to addressing this issue is to track the [[data lineage]]. Table 1 details 6 sources of data. 

A next step would be to assess the diversity of the examples by source, and then of the aggregate dataset. Further analysis of data diversity should consider the diversity of DQE in comparison to the seed tweets. It is also important to balance the diversity of the tweets with examples of quality. The paper 'Jointly Measuring Diversity and Quality and Text Generation Models' provides a useful framework for evaluating the diversity of cyberbullying dataset. This process will provide useful diagnostics for further steps. 

Another issue with the dataset is mislabeled data. I've extensively mentioned [[CleanLab]], but it would be a useful tool here as well to assess the confident join. 

The potential issues in dataset quality must be considered to develop the correct directions for study. While frustrating diagnosing and troubleshooting data quality issues is the central tenet of data-centric AI. The cyberbullying problem is perfect case study to apply and evaluate cutting edge data quality technologies. The following checklist highlights the first steps towards building our diagnostics: 
- read the 6 papers and understand data lineage
- add lineage data to each example in the dataset 
- assess diversity and quality by lineage, and of data generated through DQE 
- determine the extent of mislabeling using our pre-trained XLNet model
- use assessment to iterate on datasets and boost model performance 

The six papers cited for seed queries for DQE
- Agrawal 2018 - Deep Learning for Detecting Cyberbullying Across Multiple Social Media Platforms
- Brettschneider 2015 - Detecting Online Harassment in Social Networks
- Chatzakou 2019 - Detecting Cyberbullying and Cyberaggression in Social Media
- Davidson 2017 - Automated Hate Speech Detection and the Problem of Offensive Language
- Waseem 2016 - Hateful Symbols or Hateful People? Predictive Features for Hate Speech Detection on Twitter
- 

**Retweets Should be Removed** 
This additional preprocessing step will increase the diversity of the corpus and differentiate between an original cyberbullying tweet, and somebody simply responding to a tweet that contains cyberbullying. Idea taken from Brettschneider

https://developer.twitter.com/en/use-cases/do-research
- Twitter streaming API for better data collection than GetOldTweets3
- includes details like language of tweets and more 
- Free plan includes 500k tweets/month for testing
- Academic plan includes 10m tweets/month but requires and extensive application & approval process 