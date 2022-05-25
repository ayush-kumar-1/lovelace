# Data Quality 
Ensuring the quality of data is key to ensuring model performance, preventing data drift, and creating interpretability. 

![[Dimensions of Data Quality.png]]

Data quality has come into the forefront of the machine learning world with the rise of the [data-centric ai](https://datacentricai.org/) movement. Some examples of data-centric AI includes: 
1. [[Data Augmentation]]
2. Preventing [[Data Drift]]

## Data Quality Process 
As data scientists we shouldn't leave things up to chance. This is why I am proposing a data quality checklist. In [[The Checklist Manifesto]], Atul Gawande lays out the case for checklists. 

### 1. Understand & Define
The first step to ensuring proper data quality is to understand what the input data for a model is, and to define proper data quality for that feature. If we have tabular data we want to define the domain for a particular feature. 

### All Data Types
1. What is the datatype? Image, text, Int, float, etc. 
2. What is the data? Even if it seems obvious be precise and concise. 


### Tabular Data
Define the following for each column (including response) 

	2. Where does the data come from? Accurate lineage is key to understanding problems later in the process. Did a vendor mess up? Is someone using an adversarial example to attack our system?  
	3. Categorical, Ordinal, or Continuous? 
	4. Domain - be as narrow as possible. For categorical variables this will be a set, for continuous this will be a range.  

## Data Quality Tools 
1. [[Deequ]] (And PyDeequ)
2. [[Great Expectations]]

