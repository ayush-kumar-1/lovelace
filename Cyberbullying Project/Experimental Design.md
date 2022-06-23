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
The need for a data-centric approach to cyberbullying classification was apparent to us even in the early stages of this project, but most of our early focus was on removing noise (tweets from other languages, spam tweets, etc.). While this approach yielded mild improvements in model performance it does not resolve the key issues of data. Knowing what we know, and trying to publish a paper where the very foundations are shaky is not how I want to begin my academic career.

## Reducing/Eliminating Label Noise

## Humans-In-The-Loop Systems/Active Learning
## Rich Tweet Embeddings by Leveraging Graph Neural Networks 

[^1]: SOSNet: A Graph Convolutional Network Approach to Fine-Grained Cyberbullying Detection
[^2]: E. Englander, E. Donnerstein, R. Kowalski, C. A. Lin, and K. Parti, “Defining Cyberbullying,” _Pediatrics_, vol. 140, no. Supplement_2, pp. S148–S151, Nov. 2017, doi: [10.1542/peds.2016-1758U](https://doi.org/10.1542/peds.2016-1758U).
[^3]: J.-M. Xu, K.-S. Jun, X. Zhu, and A. Bellmore, “Learning from Bullying Traces in Social Media,” in _Proceedings of the 2012 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies_, Montréal, Canada, Jun. 2012, pp. 656–666. Accessed: Jun. 10, 2022. [Online]. Available: [https://aclanthology.org/N12-1084](https://aclanthology.org/N12-1084)
[^4]: Z. Waseem, “Are You a Racist or Am I Seeing Things? Annotator Influence on Hate Speech Detection on Twitter,” in _Proceedings of the First Workshop on NLP and Computational Social Science_, Austin, Texas, Nov. 2016, pp. 138–142. doi: [10.18653/v1/W16-5618](https://doi.org/10.18653/v1/W16-5618).