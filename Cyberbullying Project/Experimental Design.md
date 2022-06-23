# Problem Statement 
Cyberbullying detection suffers from many dataset quality issues, the largest of which has traditionally been class imbalance. This problem is exacerbated when discussing the fine-grained problem. Wang et. al[^1] tried to address this problem by using a dynamic query expansion procedure, but upon close inspection this procedure has resulted in a large amount of tweets being mislabeled. Preliminary testing on the dataset reveals anywhere from 10-15% of all examples are labeled incorrectly. Mislabeled data is present throughout all 6 classes, but is most prevalent around the "other" and "not cyberbullying" classes. 

Another issue in the dataset is the conflation of bullying traces with instances of cyberbullying. Cyberbullying[^2] is defined as


[^1]: SOSNet: A Graph Convolutional Network Approach to Fine-Grained Cyberbullying Detection
[^2]: E. Englander, E. Donnerstein, R. Kowalski, C. A. Lin, and K. Parti, “Defining Cyberbullying,” _Pediatrics_, vol. 140, no. Supplement_2, pp. S148–S151, Nov. 2017, doi: [10.1542/peds.2016-1758U](https://doi.org/10.1542/peds.2016-1758U).