# Problem Statement 
Cyberbullying detection suffers from many dataset quality issues, the largest of which has traditionally been class imbalance. This problem is exacerbated when discussing the fine-grained problem. Wang et. al[^1] tried to address this problem by using a dynamic query expansion procedure, but upon close inspection this procedure has resulted in a large amount of tweets being mislabeled. Preliminary testing on the dataset reveals anywhere from 10-15% of all examples are labeled incorrectly. Mislabeled data is present throughout all 6 classes, but is most prevalent around the "other" and "not cyberbullying" classes. 

Another issue in the dataset is the conflation of bullying traces with instances of cyberbullying. Cyberbullying[^2] definitions conflict, but primarily agree that it involves the "willful and repeated harm inflicted through the use of computers, cell phones, or other electronic devices." Bullying is a multifaceted action often involving parties beyond the perpetrator and victim, as can be seen in the diagram from  Xu et. al[^3]. Participants in a bullying episode often post on social media creating **bullying traces**. These can include reporting a bullying instance, accusing someone as a bully, revealing self as victim, and cyberbullying direct attacks. The following example displays how bullying traces have been misclassified as cyberbullying. Imagine trying to voice your pain, and then getting taken down for harassment. 

Revealing self as victim, label - **age**
> new class and then this girl just interrupted me and said "you're gay" in front of everybody I never got bullied or anything and yet that ONE MOMENT was the turning point for ruining the first half of high school for me. kids are so mean and for WHAT?!?!


![[Pasted image 20220623184656.png]]
The domains of hate speech detection, abusive language detection, and detecting bullying traces are adjacent but distinct tasks from cyberbullying detection. Mislabeled data is the single greatest issue, and even manual annotation is flawed[^4]. Zeerak Waseem used expert analysis to find serious issues with mislabeled data in his own dataset. The original Waseem dataset also happens to be the most significant dataset used in Wang's paper (greatest number of tweets). The annotator bias problem is neatly summed with the following graphic. Cyberbullying classification is a hard problem even for humans. 
![[Pasted image 20220623190521.png]]
Another key issue with the FGCD dataset is the lack of diversity in examples, and mislabeling of retweets as instances of cyberbullying themselves. The following screenshot of the dataset neatly illustrates my point. This lack of diversity if prevalent throughout all classes in the dataset. This is most likely a byproduct of the dynamic query expansion process. A common approach in the literature is to simply remove retweets and quote tweets from the dataset. 
![[Pasted image 20220623190838.png]]
In a few words, cyberbullying detection faces sparse data, data mislabeling by humans and machines, and noisy data. Inherent problems with datasets cannot be solved by more advanced models. They will simply learn to misclassify better. 

# Potential Solutions 
The need for a data-centric approach to cyberbullying classification was apparent to us even in the early stages of this project, but most of our early focus was on removing noise (tweets from other languages, spam tweets, etc.). While this approach yielded mild improvements in model performance it does not resolve the key issues of data. Knowing what we know, and trying to publish a paper where the very foundations are shaky is not how I want to begin my academic career. I layout three potential solutions to key issues, and at the end I will give my recommendation for project direction and experimental design. 
## Reducing/Eliminating Label Noise
If mislabeling is the key issue, then we should work to build systems to actively detect mislabeled examples. Unsupervised detection of corrupted labels is a topic that has exploded recently, particularly in the subfield of image classification. Many techniques[^5] have shown promise in improving model accuracy even with a high degree of mislabeled data. Much of this research has not been applied to NLP tasks, creating a niche contribution for us to leverage. 

There are many approaches to the noisy learning problem, the first being estimating $T$, the noise transition matrix. Let $X$ represent the feature space, $Y, \tilde Y$ represent the true and noisy label space respectively. 

An example $x$ is considered to be mislabeled if the given label $y_i \neq Y$ the true label. For a given $c$-class classification problem we can estimate the probability that that an example with class label $c_i$ will we inaccurately flipped to class label $c_j$. This is known as the transition probability, it can be read as the probability that class label $c_i$ will be mislabeled as $c_j$. The transition matrix $T$ consists of all such probabilities. 
$$T_{ij} = p(\tilde y = c_j, y = c_i |x)$$
For a binary classification problem we may have a $[0,1]$ label corresponding to not cyberbullying and cyberbullying respectively. We may have a sample transition matrix
$$T = \left[ \begin{matrix\right]$$

## Humans-In-The-Loop Systems/Active Learning
## Rich Tweet Embeddings by Leveraging Graph Neural Networks 

[^1]: SOSNet: A Graph Convolutional Network Approach to Fine-Grained Cyberbullying Detection
[^2]: E. Englander, E. Donnerstein, R. Kowalski, C. A. Lin, and K. Parti, “Defining Cyberbullying,” _Pediatrics_, vol. 140, no. Supplement_2, pp. S148–S151, Nov. 2017, doi: [10.1542/peds.2016-1758U](https://doi.org/10.1542/peds.2016-1758U).
[^3]: J.-M. Xu, K.-S. Jun, X. Zhu, and A. Bellmore, “Learning from Bullying Traces in Social Media,” in _Proceedings of the 2012 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies_, Montréal, Canada, Jun. 2012, pp. 656–666. Accessed: Jun. 10, 2022. [Online]. Available: [https://aclanthology.org/N12-1084](https://aclanthology.org/N12-1084)
[^4]: Z. Waseem, “Are You a Racist or Am I Seeing Things? Annotator Influence on Hate Speech Detection on Twitter,” in _Proceedings of the First Workshop on NLP and Computational Social Science_, Austin, Texas, Nov. 2016, pp. 138–142. doi: [10.18653/v1/W16-5618](https://doi.org/10.18653/v1/W16-5618).
[^5]: H. Song, M. Kim, D. Park, Y. Shin, and J.-G. Lee, “Learning from Noisy Labels with Deep Neural Networks: A Survey.” arXiv, Mar. 09, 2022. doi: [10.48550/arXiv.2007.08199](https://doi.org/10.48550/arXiv.2007.08199).