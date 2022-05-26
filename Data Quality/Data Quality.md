# Data Quality 
## Why Data Quality?
The field of machine learning is built upon the assumption that we can use examples to train statistical models to pick up on patterns. If patterns within the data are unclear, or a product of pure randomness then our models are useless. Real-world data is messy, and the signals we want to pick up are confounded in our data. Poor data quality will only add to this problem. The latest deep learning architecture may offer a marginal improvement in signal processing capability, but oftentimes at the cost of computationally complexity and loss of explainability. 

[Andrew Ng Launches A Campaign For Data-Centric AI (forbes.com)](https://www.forbes.com/sites/gilpress/2021/06/16/andrew-ng-launches-a-campaign-for-data-centric-ai/?sh=7e91c92a74f5)

>“The model and the code for many applications are basically a solved problem, Now that the models have advanced to a certain point, we got to make the data work as well.” - Andrew Ng

Andrew Ng posits that we spend nearly 80% of our time on data preparation, so we should spend 80% of our modeling efforts on boosting data quality. Domain expertise is cheaper than Machine Learning expertise, and therefore most practitioners have a much better understanding of the data vs. the SOTA algorithm. Leveraging the available expertise is a more efficient way to make models better. In short better data quality
	1. Improves model performance and assessment capabilities 
	2. Leverages an organizations' existing small datasets and domain expertise 
	3. Allows for implementation of more parsimonious (smaller) models potentially yielding greater interpretability 
	4. Improves data governance - make sure your data is ethical and unbiased

## What is Data Quality?
Ensuring the quality of data is key to ensuring model performance, preventing data drift, and creating interpretability. d

![[Dimensions of Data Quality.png]]

Data quality has come into the forefront of the machine learning world with the rise of the [data-centric ai](https://datacentricai.org/) movement. Some examples of data-centric AI includes: 
1. [[Data Augmentation]]
2. Preventing [[Data Drift]]

See more data quality techniques at [NeurIPS Data-Centric AI Workshop (datacentricai.org)](https://datacentricai.org/neurips21/)

Another idea for data quality comes from Timnit Gebru (former head Google's ethical AI division). [DataSheets](https://arxiv.org/pdf/1803.09010.pdf)
Datasheets replicate some of the data quality process, but are focused more towards academic or consumer collection settings. There are still some useful considerations present in [[DataSheets for DataSets]]. 


More ideas of data quality are implemented by AWS Sagemaker. [[Detect Pretraining Data Bias]]

***
## Data Quality Process 
As data scientists we shouldn't leave things up to chance. This is why I am proposing a data quality checklist. In [[The Checklist Manifesto]], Atul Gawande lays out the case for checklists. We can define 3 parts to our data pipelines. 
	1. Pre-modeling data quality check: ensuring our data is the highest quality needed
	2. Assessing Model Assumptions: every ml model is different, and even the same model may have different requirements by implementation
	3. Ongoing Monitoring: prevent data drift, watch out for adversarial examples (when applicable)

### 1. Understand & Define
The first step to ensuring proper data quality is to understand what the input data for a model is, and to define proper data quality for that feature. If we have tabular data we want to define the domain for a particular feature. 

#### All Data Types
1. What is the datatype? Image, text, integer, float, etc. 
2. What is the data? Even if it seems obvious be precise and concise. 
3. Where does the data come from? Accurate lineage is key to understanding problems later in the process. Did a vendor mess up? Is someone using an adversarial example to attack our system? 
4. Is our data labeled accurately? How can we check this? 
	a. [CleanLab| Labeling Errors](https://github.com/cleanlab/label-errors)
5. How much data do we need? Do we have a sufficient amount of data for the task? 

#### Tabular Data
Define the following for each column (including response) 
	1. Categorical, Ordinal, or Continuous? 
	2. Domain - be as narrow as possible. For categorical variables this will be a set, for continuous this will be a range.  
	3. Null behavior? - allowed? how to handle imputation? 
	4. What constitutes and outlier? How should outliers be handled? 
	5. Experimental Unit - What constitutes a duplicate? For longitudinal data we expect multiple observations for a product SKU and/or vendor ID, but not a combination of 3 on the same day. The same may not be true for a different application. 

#### Text Data (NLP Tasks)
Define
	1. Expected Language 
	2. Needs spellchecking? 
	3. Minimum/Maximum text length or token length
	4. What constitutes a duplicate? Do we need fuzzy matching? 
	5. How should text be cleaned? How do we know if text is clean? 
	6. Is all the data encoded in the same way?

#### Image Data 
[The 5 main metrics to assess image data quality · Cornis AI](https://ai.cornis.fr/the-5-main-metrics-to-assess-image-data-quality/)

Define
	1. What is expected image size? How will the system handle out-of-size images?
	2. How do we check for duplicates in images? 
	3. What is the expected resolution for our images? 
	4. What luminosity do we expect? 
	5. Is the image sharp enough? 

### 2. Modeling
#### Assumptions
Define
	1. Task - Classification, Regression, Image Segmentation, Sentiment Polarity, etc. 
	2. Stakes - When is it most important to be correct? When is it ok to be sacrifice performance? 
		a. It may be more important to ensure adequate transportation for a supply chain, than it is to ensure only full trucks are shipping. Think about the tradeoff between precision & recall, or between Type I and Type II errors 
	 3. Distributional Assumptions 
		 a. Does this particular model expect data from a certain distribution? i.e. Normal, Poisson, etc. 
		 b. Will the model be used for extrapolation or interpolation? Does the model suit these tasks? i.e. Gradient Boosting without tuning typically underperforms when it comes to extrapolation 
		 c. Can this model handle class imbalance? 

#### Evaluations 
1. Are there patterns in the underperformance in your model? 
	a. Is there bias based on protected categories in your model? 
	b. 
2. How can we boost performance? Data augmentation, increased labeled data, training on similar dataset? 
3. Do the benefits of boosting model performance outweigh the costs? 

### 3. Production Deployment and Ongoing Monitoring
1. Check for data drift using statistical tests of PSI and CSI. 
2. 

## Data Quality Tools 
1. [[Deequ]] (And PyDeequ)
2. [[Great Expectations]]

