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
- Are relationships between individual instances made explicit? How so? 
- Are there recommended data splits? (training, development/validation, testing)? Why so? 
- Are there any errors, sources of noise, or redundancies in the dataset? How do we know? 
- Is the dataset self-contained, or does it link to or otherwise rely on external sources? 
	a) If so, are there guarantees that they will exist, and remain constant, over time? 
	b) are there official archival versions of the complete dataset? 
	c) are there restrictions associated with any of the external resources that might apply to a future user? 
	d) provide links and access instructions to external resources 

- Does the dataset contain data that might be considered confidential? 
- Does the dataset contain data that if viewed directly, might be offensive, insulting, threatening, or might otherwise cause anxiety? 
- Does the dataset relate to people? If yes, answer the following 
	- Does the dataset identify any subpopulations? 
	- Is it possible to identify individuals, either directly or indirectly? 
	- Does the dataset contain data that might considered sensitive in any way? 
- Any other comments? 

### Collection Process 
- How was the data associated with each instance acquired? 
- What mechanisms or procedures were used to collect the data? How are these mechanisms validated? 
- If the dataset is a sample from a larger set what was the sampling strategy? 
- Who was involved in the data collection process and how were they compensated? 
- Over what timeframe was the data collected? 
- Were any ethical review processes conducted? 
- Does the dataset relate to people? 
	- Did you collect the data from the individuals directly, or obtain it via third parties or other sources? 
	- Were the individuals notified about the data collection? 
	- Did the individuals consent to the collection and use of their data? 
	- If consent was obtained, were the consenting individuals provided with a mechanism to revoke their consent in the future or for certain uses? 
	- Has an analysis of the potential impact of the dataset and its use on data subjects been conducted? 
- Any other comments? 
### Preprocessing/Cleaning/Labeling
- Was any preprocessing/cleaning/labeling of the data done? 
- Was the raw data saved in addition to the clean data? (to support unanticipated future uses)
- Is the software used to clean the instances available? 
- Any other comments? 

### Uses
- Has the dataset been used for any tasks already? 
- Is there a repository that links to any or all papers or systems that use the dataset? 
- What (other) tasks could the dataset be used for? 
- Is there anything about he composition of the dataset or the way it was collected and preprocessed/cleaned/labeled that might impact future uses? 
- Any other comments? 

### Distribution 
- Will the dataset be distributed to third parties outside of the entity on behalf of which the dataset was created? 
- How will the dataset be distributed? (tarball, api, github, database)
- When will the dataset be distributed? 
- Will the dataset be distributed under a copyright or other intellectual property (IP) license, and/or under applicable terms of use (TOU). 
- Have any third parties imposes IP-based or other restrictions on the data associated with the instances? 
- Do any export controls or other regulatory restrictions apply to the dataset or the individual instances? 
- Any other comments? 

### Maintenance 
- Who will be supporting/hosting/maintaining the dataset? 
- How can the owner/curator/manager of the dataset be contacted (e.g. email address)? 
- Is there an erratum? 
- Will the dataset be updated (e.g. to correct labeling errors, add new instances, delete instances)? 
- If the dataset relates to people, are there applicable limits on the retention of the data associated with the instances? 
- Will older versions of the dataset continue to be supported/hosted/maintained? 
- Any other comments? 