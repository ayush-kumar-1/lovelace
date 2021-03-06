---
tags: 
- capstone
- publishing
---
# Comments & Recommendations from Jamell
## Big Picture Feedback 
Jamell is a fellow intern, and 4th year PhD student at MSU. We discussed my ambitions in data science and in the field of research, and he critiqued our project. Overall feedback: we have a solid kernel of an idea, and our results are promising, but our paper is very clearly novice and needs work. For a class project we did excellent (he said 16-17 out of 20), but we need to put in a great amount of work to bring it to publishable quality. This process will most likely take many hours, but with proper support and adequate effort, we should be able to publish. There are some conferences/workshops coming up soon, so we have around a month to make a real push to get our paper to publishable quality. 

### Writing is Stylistically Fragmented and of Poor Quality 
Our writing was done for the most part within a matter of a few days, and it shows. It is apparent that there were 3 different authors on the paper, and it lacks stylistic cohesion. Our writing is at times overly descriptive, and at other times not descriptive enough. 

Much of our project was written in context of the requirements of the capstone project. We adhered to this well for our purposes, but in a research context we must improve the quality of the writing. 

When we submit to a workshop/conference/journal our paper will be reviewed by people who have studied the subject for 5 years, 10 years or even longer. If our information is not 100% correct, or there is room for doubt we place ourselves at high risk for rejection. We must have perfect confidence in our ideas, and convey them clearly and concisely.  

**How do we make our writing better?**

Read, read, read. The more cyberbullying and hate speech papers we consume, the better idea we get of the lexicon of the topic, and the structure of the papers. Every topic within ML has a slightly different conventions and vocabulary we must familiarize ourselves with. 

Avoid the universal 'we' for the most part. Overall we have to learn how to tell a coherent story. We need to focus on the rewrite portion as follows: 
1. Research - read, read, read 
	Consuming as much as possible and rewriting our related works is the top priority
2. Remove Content 
	Anything that is standard in the industry must go. We need to know what to get rid of
3. Intro should be written second to last, abstract should be written very last 
4. Expand on results, discussion, and conclusion

### Introduction & Related Works Lack Detail 
Our related works section is sparse, and lacks the necessary detail needed to effectively tell a story. Related works should be comprehensive review of the subject, its importance, and our inspiration for research. We should a minimum of 15+ citations in this section (we currently have 2). This should also be our starting point for improvement for a few key reasons
- related works forces you to review the current literature in depth around the subject 
- it allows for better contextualization of our contribution to the literature 

### Modeling 
Our modeling needs work. In essence we cannot use traditional statistical models as anything but a baseline for more complicated transformer architectures. We can also not "bash" our own paper in our comparisons to Ahmed in section 8. Jamell recommended we utilize at least 3 (maybe 4) neural networks in our paper. Potential architectures included: 

1. [[DistilBERT]]
2. [[HateBERT]]
3. [[RoBERTa]]

We don't need to get rid of XLNet, and we can get away with not including BERT because we have all these variants as well. Another idea would be to utilize BERT as our baseline for the other models. Further research is required. Bottom line - we have no chance of pushing out a paper with a single deep learning model when the previous literature used multiple, and had better overall results (even with questionable methodology). 

We also do not spend much time optimizing the hyperparameters of XLNet. At minimum we should be giving a search across a sample space to optimize for batch size, and potentially decreasing the learning rate, and letting the model train for longer. We can also tinker around with the number of hidden layers to optimize results. AT minimum we must test various batch sizes (16, 32, 64), and find the ones that work the best. Smaller batch sizes don't generalize as well, but our dataset is also very small in the grand scheme of things. 

**What about computational complexity?**

Hyperparameter tuning multiple large language models required either a large amount of time, or large amount of distributed computing resources. We need to discuss this point with Dr. Mandal and the stat or CS department to get access to a cluster. If UGA won't help us, Jamell discussed utilizing his access to the MSU clusters for running our models. 

### Embedding and Classification Methods are Too Detailed
Understanding which details to include, and which ones to exclude is difficult, but it is dependent on the standards for the task that your are publishing. In the cyberbullying/nlp field we don't need to expand on BOW, or TF-IDF, and we can keep our descriptions of neural models to a minimum. Jamell proposed that we take our sections 5 and 6, combine them and lay them out as so...

5. Classification Methods
	5.1 -  Feature Extraction 
		5.1.1 - BOW
		5.1.2 - TF-IDF
	5.2 - Baseline models 
		5.2.1 - SVM or LR
		5.2.2 - XGBoost
	5.3 - Deep Learning Methods 
		5.3.1 - BERT 
		5.3.2 - DistilBERT 
		5.3.3 - RoBERTa
		5.3.4 - HateBERT
		5.3.5 - XLNet

When it comes to LSA, N-grams, or any other technique we tested but didn't use - take it out. If it doesn't work - exclude it. 

### Replace Wordclouds with Bar Graphs
Wordclouds are not considered professional enough for research, and sometimes are a reason to decline the paper altogether. Replacing them with bar graphs that show the top $n$ words or n-grams are more descriptive and allow for better checks of divergence. 