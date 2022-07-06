# Learning with Noisy Labels 
Deep neural networks (DNN) have a tendency to memorize and overfit. Arpit. et. al showed that DNNs will first memorize general patterns, and only later overfit on noisy labels. [@arpitCloserLookMemorization2017].  Real world data is prone is noisy labels and requires approaches leverage large-scale noisy datasets. Waseem et. al showed that cyberbullying annotations can  suffer from biased label annotations [@waseemAreYouRacist2016]. Learning with noisy labels (LNL) is a recent topic in deep learning research that attempts to limit the effect of noisy labels. Most papers divide these into two approaches, sample selection and loss function regularization. Song et. al provides a more robust survey on the topic categorizing a good portion of state-of-the-art (SOTA) approaches into five categories: robust architecture, sample selection, robust loss function, loss adjustment, and robust regularization [@songLearningNoisyLabels2022]. This document details a diverse selection of approaches in the context of automatic cyberbullying detection. The problem of text classification diverges from most of existing literature which focuses on label noise in image classification datasets, most commonly CIFAR-10, CIFAR-100, MNIST, and Clothing1M. 

The first portion of this document will lay the preliminaries for LNL problem. Then we will sample some of the approaches available to address the issue. A few studies of LNL in the text classification domain will follow. Finally, I will give my thoughts on the direction of our study including recommendations, concerns, and next steps. 

## Preliminaries 
We consider a $c$-class classification problem with a softmax output layer, so all output probabilities add up to one.  Let $\mathcal{X} \subset \mathbb{R}^d$  be the features space and $\mathcal{Y}$ be the one-hot encoded label. The clean dataset $\mathcal{D}$ is comprised of $N$ data points $(x_i, y_i)$  from an unknown joint probability distribution $\mathcal{P}_d$ where every example is independent and identically distributed.  A DNN will learn the mapping function $f$ with parameters $\Theta$ that correctly maps $f(\cdot; \Theta): \mathcal{X} \Rightarrow \mathcal{Y}$. This learning process is undertaken by minimizing the empirical risk $\mathcal{R}_D(f)$ with a given loss function, usually cross-entropy loss. 

$$\mathcal{R}_D(f) = \mathbb{E}_D[\mathscr{l}(f(x;\Theta), y)] = \frac 1 N \sum_{(x,y) \in \mathcal{D}} \mathscr{l}(f(x;\Theta), y)$$
In the noisy setting the true labels $\mathcal{Y}$ are corrupted by annotator bias, automatic labeling procedure, or by mistakes. The corrupted labels are denoted by $\tilde {\mathcal{Y}}$  and the noisy dataset by $\tilde{\mathcal{D}}$. This label noise can be characterized as *instance-independent* or *instance-dependent*. Note that we consider only *close-set* noise in which mislabeling can only belong one of the specified classes. In contrast, *open-set* noise allows for labels to belong outside of the $c$-classes in $\tilde{\mathcal{Y}}$. 

Instance-independent noise (IIN) assumes that corruption process in conditionally independent from the data features when the true label. IIN assumes that labels are flipped according to a noise transition matrix $T \in \mathbb{R}^{c \times c}$, where $T_{ij} := p(\tilde y = j|y=i)$ is the probability of the true label $i$ being flipped into a corrupted label $j$. There are three types of noise within IIN
	1. *Symmetric or Uniform Noise* in which there is an equal chance of any label $i$ being corrupted into a label $j$ with a noise rate $\tau$. $\forall_{i\neq j} T_{ij} = \frac{\tau}{c-1}$ 
	2. *Asymmetric or Label-Dependent Noise* in which certain classes are more likely to be confused than others. For example "not cyberbullying"  may be easily confused with "other cyberbullying" than "gender-based cyberbullying". 
	3. *Pair Noise* is a stricter case of asymmetric noise where a true label is flipped into only a certain different label. 
IIN can be simply generated with random label flipping procedures based on a specified noise transition matrix. 

With *Instance-Dependent Noise* (IDN) the corruption probability is assumed to be depending on both the features and the labels. This type of noise is by far more challenging to model. The corruption probability is defined as $p_{ij}(x) = p(\tilde y = j|y=i,x)$. The key difference is that mislabeling is also dependent on the features $x$. IDN is far more realistic, but more difficult to generate as well. Chen et. al attempts to address IDN with novel approaches for generation and modeling [@chenClassConditionalAssumptionPrimary2020]. The IDN generation algorithm from Chen et. al trains a DNN for multiple epochs and looks for examples where there are severe swings in predicted probabilities. This corresponds to "hard" examples which are confused more often. Other approaches involve training non small samples of data and then generalizing noise generating algorithms on that basis. 

## Robust Loss Functions & Regularization 
### AutoDO (Gudovskiy et. al)
### Augmentation Strategies (Nishi et. al)
### S-Model & C-Model (Goldberger & Ben-Reuven)
### Adversarial Training (Zhu et. al)
### SCE-Loss (Wei et. al)

## Loss Adjustment 
### SEAL (Chen et. al)
### HOC (Zhu et. al)
### MLC (Zheng et. al)

## Sample Selection 

### Confident Learning (Northcutt et. al)
Confident learning (CL) is implemented in the [[CleanLab]] library and introduced me to the idea of LNL [@northcuttConfidentLearningEstimating2021]. CL follows a data-centric approach and relies on the premise that the key to LNL lies in accurately characterizing the uncertainty of label noise in the data. CL boils down to 3 approaches. 
	1. *Prune*, searching for label errors and *soft-pruning* using loss-reweighting. *Hard-pruning* may characterized as *label refurbishment* or removing noisy examples from the training set. 
	2. *Count*, training on the clean data. 
	3. *Rank* which examples to use during training. This allows learning from unnormalized probabilities and the ideas of curriculum learning. 
Confident Learning is a framework agnostic of model choice or task at hand (so long as it is classification). 

**Test Results**
CIFAR-10 40% Asymmetric Noise - 87.2% 
CL was also tested on the Amazon reviews dataset with varying amounts of label noise, and showed 5-6% accuracy improvements over baseline. 

### Co-Teaching (Han et. al) & Co-Teaching+ (Yu et. al)
Co-Teaching (COT) [@hanCoteachingRobustTraining2018] builds off of MentorNet [@jiangMentorNetLearningDataDriven2018] and decoupling with an iteration on multi-network learning for noisy labels. The goal is for the twin networks to select clean samples based on a pre-trained network. This is very similar to ideas found within active learning where after a certain amount of random examples are labeled, certain data are chosen for labeling. The two-network approach makes sense so long as the two networks are learning independently. The networks receive independent mini-batches of data $b_f, b_g$. The two classifiers $f, g$ then pick examples for the other to learn from based on small-loss instances from their respective mini-batches. Thus, classifier $f$ is updated with small-loss instance from $b_g$ and classifier $g$ is updated with small-loss instances from $b_f$. This exchanging process is the backbone of COT. 

When students write essays or work on assignments alone they may be blind to certain mistakes they repeatedly make. For example, my grammar has remained consistently horrendous even as my prose has improved. Another student may be blind to other kinds of mistakes. When we check each others works both of us become much stronger. This is the intuition behind the student-teacher approach. The dual networks are better equipped to find different kinds of label noise and correct learning. 

**Test Results**
CIFAR-10 45% Pair Noise - 75.42%
CIFAR-10 50% Symmetric Noise - 74.02% 

Co-Teaching+ (COT+) 

### JoCoR (Wei. et. al)
### DivideMix (Li et. al)
