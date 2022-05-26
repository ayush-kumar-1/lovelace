# Data Sheets for DataSets
> DATA PLAYS A critical role in machine learning. Every machine learning model is trained and evaluated using data, quite often in the form of static datasets. The characteristics of these datasets fundamentally influence a model’s behavior: a model is unlikely to perform well in the wild if its deployment context does not match its training or evaluation datasets, or if these datasets reflect unwanted societal biases. Mismatches like this can have especially severe consequences when machine learning models are used in high-stakes domains, such as criminal justice,1,13,24 hiring,19 critical infrastructure,11,21 and finance.18 Even in other domains, mismatches may lead to loss of revenue or public relations setbacks. Of particular concern are recent examples showing that machine learning models can reproduce or amplify unwanted societal biases reflected in training datasets. - Gebru et. al

The objective of datasheets for datasets is to address the needs of dataset creators and consumers in a standardized way to ensure best practices in order prevent training bias. Well documented data is also key to MLOps. Gebru lays out a few key insights: 
	1. There are no industry standards for documenting ML datasets. 
	2. Datasheets address this gap by documenting the contexts and contents of datasets. 
	3. Datasheets increase transparency and accountability. Mitigate unwanted bias, facilitate reproducibility, and help researchers and practitioners choose the right dataset. 
	4. Datasheets encourage intentionality throughout the dataset creation process. 
	5. Iterating on design for in particular contexts with help from practitioners and legal experts will improve questions. 
	6. Datasheets are part of an increasing trends towards standardized reproducible ML development. 
	7. Gebru insists that datasheets template are **NOT** meant to be a one size fits all checklist. 

## Proposed Question Template 
### Motivation 
• For what purpose was the dataset created? Was there a specific task in mind? Was there a specific gap that needed to be filled? Please provide a description.
• Who created the dataset (e.g., which team, research group) and on behalf of which entity (e.g., company, institution, organization)? 
• Who funded the creation of the dataset? If there is an associated grant, please provide the name of the grantor and the grant name and number.
• Any other comments?

### Composition 
- What do the instances that comprise the dataset represent? Are there multiple types of instances?
- How many instances are there in total? 
- Does the dataset contain all possible instances? or is it a sample of instances from a larger set? 
- What does each instance consist of? Raw data? Features? 
- Is there a label or target associated with each instance? 
- Is any information missing for individual instances? 
- 