# Problem Statement 
Cyberbullying detection suffers from many dataset quality issues, the largest of which has traditionally been class imbalance. This problem is exacerbated when discussing the fine-grained problem. Wang et. al[^1] tried to address this problem by using a dynamic query expansion procedure, but upon close inspection this procedure has resulted in a large amount of tweets being mislabeled. Preliminary testing on the dataset reveals anywhere from 10-15% of all examples are labeled incorrectly. Mislabeled data is present throughout all 6 classes, but is most prevalent around the "other" and "not cyberbullying" classes. 

Another issue in the dataset is the conflation of bullying traces with instances of cyberbullying. Cyberbullying[^2] definitions conflict, but primarily agree that it involves the "willful and repeated harm inflicted through the use of computers, cell phones, or other electronic devices." Bullying is a multifaceted action often involving parties beyond the perpetrator and victim, as can be seen in the diagram from  Xu et. al[^3]. Participants in a bullying episode often post on social media creating **bullying traces**. These can include reporting a bullying instance, accusing someone as a bully, revealing self as victim, and cyberbullying direct attacks. The following example displays how bullying traces have been misclassified as cyberbullying. 

Revealing self as victim, label - **age**
> new class and then this girl just interrupted me and said "you're gay" in front of everybody I never got bullied or anything and yet that ONE MOMENT was the turning point for ruining the first half of high school for me. kids are so mean and for WHAT?!?!



![[Pasted image 20220623184656.png]]
The domains of hate speech detection, abusive language detection, and detecting bullying traces are adjacent but distinct tasks from cyberbullying detection. Mislabeled data is the single greatest issue, and even manual annotation is flawed. 

[^1]: SOSNet: A Graph Convolutional Network Approach to Fine-Grained Cyberbullying Detection
[^2]: E. Englander, E. Donnerstein, R. Kowalski, C. A. Lin, and K. Parti, “Defining Cyberbullying,” _Pediatrics_, vol. 140, no. Supplement_2, pp. S148–S151, Nov. 2017, doi: [10.1542/peds.2016-1758U](https://doi.org/10.1542/peds.2016-1758U).
[^3]: J.-M. Xu, K.-S. Jun, X. Zhu, and A. Bellmore, “Learning from Bullying Traces in Social Media,” in _Proceedings of the 2012 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies_, Montréal, Canada, Jun. 2012, pp. 656–666. Accessed: Jun. 10, 2022. [Online]. Available: [https://aclanthology.org/N12-1084](https://aclanthology.org/N12-1084)