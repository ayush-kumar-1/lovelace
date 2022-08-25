Machine learning assumes that data can be used to train statistical models to pick up on patterns**. When patterns are unclear our models are at best useless, and at worst harmful.** Real-world data is messy, and signals can be hard to identify. Poor data quality greatly exacerbates this problem. State-of-the-art deep learning architecture may offer a marginal improvement in signal processing capability, but at the cost of increased computationally complexity and loss of explainability. The [data-centric AI](https://datacentricai.org/) movement was founded by Andrew Ng on the belief that better data is the next step to better AI.

**“The model and the code for many applications are basically a solved problem, Now that the models have advanced to a certain point, we got to make the data work as well.” - Andrew Ng**

 Data quality is a multidimensional issue ranging from simple validation to detecting intersectional biases. Many businesses are familiar with common sense pre-training data validation; what is referred to as **data quality.** Data quality and data-centric AI go beyond data quality and ask questions about the distribution of the dataset. **Data distribution quality** encompasses testing and validating the statistical assumptions made during pre-training, modeling, and deployment. **Data documentation** allows for all aspects of data and model quality to be communicated across silos reducing technical debt. This whitepaper focuses on **data quality for tabular**, but general principles are applicable to other datatypes as well.
   

## Data Quality

“Data Quality” contains most traditional aspects of data security. Is this data fundamentally correct? Creating & enforcing expectations for data quality are a key tool for data validation and data verification[[KA1]](#_msocom_1) .

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image002.jpg)

Data distribution quality is the focus of this document and refers to the statistical assumptions around the dataset and model. Data distribution quality can be broken down into 3 main components: 1) Pretraining, 2) Model Development, and 3) Deployment and monitoring. At each step the distributional qualities of the data must be assessed and validated in context. The following is a sample checklist of potential issues to consider. Every model may handle data differently, and its unique characteristics should be considered.

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image004.png)

Dataset and model documentation facilitate communication across silos and teams. A single project may need to communicate with multiple teams, and those teams may change over time. Standardized documents enforce a common language across the business to understand data science projects, use cases, and implementations. Current documentation standards are under development and include:

**Datasheets for Datasets[**[1]**](#_ftn1)**: The number of stake holders that need to understand a particular aspect of the data pipeline is large and everchanging. Datasheets help all stakeholders understand the data they are using. It also forces teams consider multiple aspects of their data. Areas covered include task motivation, dataset composition, data collection process, preprocessing/cleaning/labeling, data uses, dataset distribution, and maintenance.

**Model Cards[**[2]**](#_ftn2)**: Model cards standardize model documentation across use cases. This includes basic facts including which model(s) was used, how it was parametrized, performance, and evaluations for fairness.

# Data Quality Tools

**Great Expectations** [[KA2]](#_msocom_2) is a data quality tool created to enforce various constraints on a single or multiple columns of data. There is a large community developing expectations for rigorous statistical tests for tabular, geospatial, text, and image data.

Deequ[[3]](#_ftn3) is an open-source data quality software developed by amazon. PyDeequ[[4]](#_ftn4) is a python wrapper for Deequ. There are 3 main components to Deequ:

1.       **Metrics Computation** – Statistical metrics to measure the health and validity of your data. These can be as simple as mean, median, mode or as complicated as needed for assessing distributional qualities of your data.

2.       **Constraint Verification** – Validating the data that is being streamed into your applications to make sure it matches your expectations.

3.       **Constraint Suggestion** – Use automated constraint suggestion methods to profile your data and build expectations.

Deequ is implemented on top of **Apache Spark** and is designed to scale with large datasets that typically live in a distributed filesystem or a data warehouse.

Mislabeled data greatly impacts model performance and evaluations. Unfortunately, mislabeling is pervasive even in academic settings[[5]](#_ftn5). Manual label validation is labor intensive and infeasible in most contexts. [**CleanLab**](https://docs.cleanlab.ai/v2.0.0/index.html)[****[6]****](#_ftn6) provides a suite of tools for **finding and fixing potential label errors.** Better labels cut through confusing signals in training and validation data leading to better model performance. More accurate testing labels provide better model evaluation. The release of CleanLab 2.0 expands opportunities to productionalize label correction with just a few lines of code.

![9 examples label errors in the MNIST dataset](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image006.png)

Labelbox[[7]](#_ftn7) is an enterprise tool for active learning, data labeling, and annotation. Kimberly-Clark has access to Labelbox for improving text and image labels. Labelbox provides an end-to-end system for improving model performance. Improving labels, versioning data, and leveraging automation make Labelbox more than a simple data annotation app.

# Data Quality

To ensure data meets quality and governance guidelines, the guidelines must first be defined. Building expectations requires understanding the business task and goal. Once the ML task has been defined the data lineage should be cataloged. **Data lineage** [[KA3]](#_msocom_3) tracks the flow of data from data ingestion/creation all the way to model deployment. Every column should have its lineage tracked including all preprocessing tasks.

# Data Distribution Quality

Generic data quality constraints and expectations are a solid foundation to building good models, but every model may have different constraints and requirements. It’s important to choose the correct model for the task: interpolation or extrapolation? Is the quantity of quality data enough for this model? Are there additional constraints on data that the model enforces? i.e., no endogeneity, data following a certain distribution, etc. Testing for these assumptions will lead to better model selection, avoiding overfitting, and selecting a model with an appropriate level of interpretability.

Additional data-centric considerations include, but are not limited to:

·       What level of performance is required to move forward to deployment?

·       Has the model been stress-tested against out-of-sample behavior?

·       Has the model been stress-tested against spurious correlations?

·       Are there patterns in model underperformance?

·       Has the model been stress-tested against bias? (Models can in theory produce biased predications even with strong pre-training checks)

·       Can model performance be boosted with synthetic data or producing more labeled data?

·       What range should model predictions be in?

Stress-testing models produces robust predictions and can help prevent unwanted behaviors before they occur in the real world. Picking up on extreme behaviors or potential biases ensures that the model is equipped for the uncertainty in the real world.

## Data Distribution Distance Measures

Assessing model assumptions, measuring bias, and detecting data drift all rely on accurately being able to **detect the difference between two statistical distributions**. When the target distribution is known (i.e., assessing normality for a linear model) parametric statistical tests can be used. Oftentimes the underlying distribution of the data is unknown, or it is infeasible to build customized tests for ever column of the data. Nonparametric tests are uses in this case.

Kullbeck-Leibler Divergence, Population Stability Index, and Jensen-Shannon Divergence are **nonparametric tests for discrete random variables.**

Kolmogorov-Smirnov Test, Mann-Whitney U Test, and the Cucconi test are **nonparametric tests for continuous random variables.**

The Anderson-Darling Test, Jarque-Bera Test, and Shapiro-Wilk Test **are parametric tests for normality.**

While the above tests are by no means a comprehensive review, they provide a solid starting point for distributional measures. Each test has its strengths and limitations, and some applications may benefit from more careful applications of tests. In others general monitoring maybe sufficient. If unsure here are general recommendations for evaluation:

**Case**

**Test/Measure**

2 independent discrete random variables

Population Stability Index

2 independent continuous distributions

Kolmogorov-Smirnov Test

1 variable assessment of normality 

Shapiro-Wilk Test

###  

### Kullbeck-Leibler Divergence

Discrete random variables provide a much simpler methodology for measuring divergence. Kullbeck-Leibler divergence (or relative entropy) provide a simple measure of divergence between two probability distributions. KL divergence is also well defined for the parametric continuous case but breaks down in the nonparametric case. The formula for KL divergence is as follows in the discrete case.

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image008.png)

 In the continuous case we simply model this utilizing an integral. An important characteristic of KL divergence is that it is not symmetric. In general, this means that

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image010.png)

KL divergence can be implemented with SciPy: [scipy.special.rel_entr — SciPy v1.8.1 Manual](https://docs.scipy.org/doc/scipy/reference/generated/scipy.special.rel_entr.html#scipy.special.rel_entr). [[KA4]](#_msocom_4) Note that the scipy.special.kl_div is NOT the formula provided above, it adds two extra terms.

KL divergence is a measure of distance with 0 representing identical distributions, and larger values signaling larger divergences. KL divergence will always be non-negative, and there is no theoretical upper bound. It can be difficult to interpret and determine cut-offs for divergence based on KL divergence.

### Population Stability Index

We can consider the symmetric version of the KL divergence as

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image012.png)

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image014.png)

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image016.png)

This symmetrical KL divergence is known as the **Population Stability Index**. The PSI provides one key advantage of the KL Divergence which is a known distribution[[8]](#_ftn8). Through a Taylor series expansion, it can be shown that PSI approximately follows a chi-squared distribution which allows us to conduct the following hypothesis test:

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image018.png)

The null is rejected if

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image020.png)

Where n is the number of samples from P, m is the number of samples from Q, alpha is the probability of type 1 error, and B is the number of levels in the data.

### Jensen-Shannon Divergence

The Jensen-Shannon divergence (JS) measures how much the label distributions of different facets diverge from each other entropically. It is based on the Kullback-Leibler divergence, but it is symmetric.

The formula for the Jensen-Shannon divergence is as follows:

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image022.png)

The range of JS values for binary, multicategory, continuous outcomes is ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image024.png).

-   Values near zero mean the variables are similarly distributed.
-   Positive values mean the distributions diverge, the more positive the larger the divergence.

This metric indicates whether there is a big divergence in one of the labels across facets

### LP-Norm

The ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image026.png)-norm (LP) measures the p-norm distance between two distributions of a variable. This metric is non-negative and so cannot detect reverse bias.

The formula for the ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image026.png)-norm is as follows:

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image028.png)

The norm measures the distance between two vectors.

### Total Variation Distance

The total variation distance data bias metric (TVD) is half the L1-norm. The TVD is the largest possible difference between the probability distributions for label outcomes of facets _a_ and _d_. The L1-norm is the Hamming distance, a metric used compare two binary data strings by determining the minimum number of substitutions required to change one string into another. If the strings were to be copies of each other, it determines the number of errors that occurred when copying. In the bias detection context, TVD quantifies how many outcomes in facet _a_ would have to be changed to match the outcomes in facet _d_.

The formula for the Total variation distance is as follows:

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image030.png)

For example, assume you have an outcome distribution with three categories, ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image032.png) in a college admissions multicategory scenario. You take the differences between the counts of facets _a_ and _d_ for each outcome to calculate TVD. The result is as follows:

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image034.png)

Where:

-   ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image036.png) is number of the ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image038.png) category outcomes in facet _a_: for example na(0) is number of facet _a_ acceptances.
-   ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image040.png) is number of the ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image042.png) category outcomes in facet ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image044.png): for example, ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image046.png) is number of facet _d_ rejections.

The range of TVD values for binary, multicategory, and continuous outcomes is ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image048.png), where:

o   Values near zero mean the labels are similarly distributed.

o   Positive values mean the label distributions diverge, the more positive the larger the divergence.

### Kolmogorov-Smirnov Test

Continuous random variables may have unknown distributions which makes testing for data drift difficult. The branch of nonparametric statistics deals with the case where the underlying distribution of a test statistic is unknown. The Kolmogorov-Smirnov test is one such nonparametric test with simple intuition – measure the maximum difference between two empirical CDF’s (or between an empirical CDF and theoretical CDF).

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image050.png)

Figure 5 - Kolmogorov-Smirnov Test Illustration

The KS-Test is built to detect the difference in distribution between two continuous distributions based on their CDF's. This can be two unknown samples (2-sample KS-Test) or a single unknown variable and a target distribution (i.e. normal, exponential, etc.) The KS test statistic can be calculated with

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image052.png)

The KS test statistic follows the Kolmogorov distribution. To conduct a KS test, simply use the SciPy library. The KS test works at very low sample sizes but is not the most powerful test for detecting normality. In the case of normal distributions, standardize the data and calculate the KS test statistic with the standard normal distribution. For large sample sizes errors may propagate, but downsampling or kernel approximation may be appropriate. KS test statistic is well defined for discrete random variables, but for discrete RVs with few levels the KL divergence may be a more appropriate measure.

### 1.1.1.            Shapiro-Wilk Test

The Shapiro-Wilk test is the most powerful test for assessing normality. It tests the null hypothesis ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image054.png), that a sample ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image056.png)came from a normally distributed population. The Shapiro-Wilk Test statistic is

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image058.png)

The cutoff values and test statistic are typically computed using statistical software like SciPy.

### Class Imbalance

Class imbalance measures which classes have fewer training samples based on a characteristic. CI is important to track because models will preferentially fit the larger classes at the cost of the smaller ones. For a column of data with two values ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image060.png), ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image062.png) the CI can be calculated as ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image064.png)

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image066.png) will range from ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image068.png) with positive values representing facet ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image060.png) having more training samples, negative values indicating facet ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image062.png) has more examples.

### Label Imbalance

Label imbalance extends the idea of class imbalance to ratios of different labels. It measures the difference in proportions of labels (DPL) for an observed label ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image070.png) between two facets of a column. A machine learning model trained on this data will learn the relationship between the facets and the outcome resulting in bias. DPL can be calculated as follows.

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image072.png)

Where ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image074.png) is the number of members in facet a with given label ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image070.png). If DPL is close enough to 0 then we say that demographic parity has been achieved. For binary and multicategory labels the DPL values range from ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image076.png).

·      ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image078.png) indicates that facet a has a higher proportion of positive outcomes

·      ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image080.png) near 0 indicate a more equal proportion of positive outcomes between facets and a value of 0 indicates perfect demographic parity

·      ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image082.png) indicates that facet ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image062.png) has a higher proportion of positive outcomes when compared with facet ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image060.png)

# Detecting Bias [[KA5]](#_msocom_5) 

              Unintentional bias in AI is a negative externality on marginalized groups and a regulatory risk. Despite bureaucratic lag the number of AI-related lawsuits has greatly increased. George Washington University has developed a [preliminary list](https://blogs.gwu.edu/law-eti/ai-litigation-database/) of such lawsuits[[9]](#_ftn9). In _Weapons of Math Destruction[**[10]**](#_ftn10)_ Cathy O’Neill details many instances of AI algorithms gone wrong. The stakes are incredibly high – a single AI lawsuit can cost millions in litigation, settlements, and damages. **One lawsuit has the potential to erase the cumulative benefits from a dozen AI initiatives**.

              When models train on biased data they learn human biases. AI’s ability to scale perpetuates these harms with incredible speed. Steps must be taken to ensure our datasets are free from bias based on protected characteristics including but limited to race, gender, sexuality, and age. Reducing bias is the morally right thing to do, but also provides protection against lawsuits and regulation. Given KC’s multinational nature navigating unintentional bias is complex problem on the intersection of law and technology. Given this complex nature the following statistical techniques to detect bias are simply tools that must be applied carefully. When in doubt legal considerations should be voiced and evaluated on a case-by-case basis. 

## Overview on Detecting Bias

The first step in detecting bias is determining the column of the interest. This column typically describes protected characteristics like sex, gender, race, or sexuality. Other sources of bias can include nationality, region, or any other category. Bias in models can extend beyond protected characteristics and show up in unexpected places. Assessing against these spurious correlations is always a good idea.

When measuring pretraining bias the different categories of a given characteristic are known as **facets**. Most of measuring pretraining bias is assessing the distributional differences between these facets.

# Data Drift

Model deployment and monitoring is of utmost important to ensure that behavior is on track. Once out in the wild, model inputs and outputs must be carefully monitored. This includes data validation, limiting access, and safeguards against adversarial examples (if applicable).

Data drift is unexpected and undocumented changes to data structure, semantics, and/or distribution that is a result of modern data architectures. Data drift breaks processes and corrupts data but can also reveal new opportunities for data use. Oftentimes the distribution of data at time of training becomes obsolete by the time production is ready for data. As we stream new data checking for changes in the distribution of data is key to preventing performance failures in your machine learning pipeline.

## Overview of Data Drift

In supervised and semi-supervised settings, observations ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image084.png) are assumed to be drawn independently from the same joint distribution ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image086.png) If data begins to diverge from this distribution our model assumptions do not hold. This is data drift. Monitoring data drift is difficult because model assumptions can vary widely and, data can range from images, text, tabular, to complicated graph structures. Formally data drift occurs when the training distribution![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image088.png) and the real-world distribution, ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image090.png) diverge.

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image092.png)

Not only can data drift mess with overall distribution, it can also violate assumptions of independence if there are external factors changing the distribution, or drift occurs in a particular direction due to macroeconomic conditions. Some causes of drift to watch out for include:

1.       Sample selection bias

2.       Non-stationary environment

**Feature drift** occurs when the underlying distribution of the feature vectors change, but the ground truth relationship between ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image094.png) and ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image096.png) remains the same. In simpler terms, data that previously was underrepresented (or not present) is observed more frequently. Formally feature drift (or covariate drift) occurs when

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image098.png)

**Concept drift** is the opposite of feature drift. The feature/covariate distributions remain the same, but the target distributions have changed. Formally concept drift occurs when

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image100.png)

**Dual drift** is when we have both feature drift and concept drift at the same time.

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image102.png)

## Detecting Data Drift

Detecting data drift on tabular data involves monitoring the distribution of production data in comparison to the training data. These differences can be monitored by the various statistical tests presented in Section 4.1 – Distributional Distance Measures. Each column can be treated as unparametrized random variable, and the model can be retrained when significant drift is detected.

## Non-Tabular Data

Detecting data drift for non-tabular datatypes is still an emerging field with no clear answers. Current approaches hinge upon using low-dimensional embeddings as proxies for catching data drifts.

# Potential Future Directions

## Bayesian Nonparametric Methods

There are 4 primary branches in statistics stemming from a combination of bayesian vs. frequentist and parametric vs. nonparametric. Frequentist statistics are taught in school - confidence intervals, hypothesis tests with p-values, and other inference models assuming that the true nature of the world is a fixed quantity to determine from observation. Bayesians believe the world to be everchanging and update their beliefs about the quantity in question as more information (data) becomes available.

 Parametric statistics is concerned with the study of models with fixed parameter values that are to be determined. Nonparameterics in contrast assumes that there are an infinite number of possible parameters that can take on almost any value that cannot be precisely determined. Frequentist and bayesian parametric statistics assume that the underlying truth is a function of a certain quantities i.e. the mean and the variance of a normal distribution. In the nonparametric world we make no such assumptions about the underlying distribution. While this generalization makes things more difficult, it oftentimes more accurately reflects the uncertainty in distributional qualities that real world data exhibits.

Possible directions for concept drift detection come from bayesian nonparameterics including Dirichlet processes, Gaussian mixture models, and polya tree tests[[11]](#_ftn11).

  

---

[[1]](#_ftnref1) [Datasheets for Datasets](https://arxiv.org/abs/1803.09010) – Gebru et. al. 2021

[[2]](#_ftnref2) [Model Cards for Model Reporting](https://arxiv.org/abs/1810.03993) – Mitchell et. al. 2019

[[3]](#_ftnref3) [Test data quality at scale with Deequ | AWS Big Data Blog (amazon.com)](https://aws.amazon.com/blogs/big-data/test-data-quality-at-scale-with-deequ/)

[[4]](#_ftnref4) [PyDeequ GitHub](https://github.com/awslabs/python-deequ)

[_**[5]**_](#_ftnref5) [_Pervasive Label Errors in Test Sets Destabilize Machine Learning Benchmarks_](https://arxiv.org/abs/2103.14749)_,_ Northcutt et. al. 2021

[[6]](#_ftnref6) [Cleanlab](https://cleanlab.ai/)

[[7]](#_ftnref7) [Labelbox: the leading training data platform for production AI](https://labelbox.com/)

[[8]](#_ftnref8) [Statistical Properties of Population Stability Index](http://www.stat.wmich.edu/naranjo/PSI.pdf), Naranjo. 2018

[[9]](#_ftnref9) Ethical Tech Initiative of DC, Professor Robert Brauneis. 2021

[[10]](#_ftnref10) [Weapons of Math Destruction - Wikipedia](https://en.wikipedia.org/wiki/Weapons_of_Math_Destruction)

[[11]](#_ftnref11) [Bayesian Nonparametric Unsupervised Concept Drift Detection for Data Stream Mining | ACM Transactions on Intelligent Systems and Technology](https://dl.acm.org/doi/10.1145/3420034)

---

 [[KA1]](#_msoanchor_1)Add two things – differentiate from data sanity and data quality. Validation vs. pure quality. Don’t got too much in detail about how to do it. In the overview give each equal.

1.       General Overview 

2.       Data Distribution Quality 

3.       Data documentation and data quality

 [[KA2]](#_msoanchor_2)Why is GE any better than other tools? Show the report generation features? KC and DataBricks recommended tool.

 [[KA3]](#_msoanchor_3)Add into the data documentation efforts/section.

 [[KA4]](#_msoanchor_4)What is considered good/bad? Does not need to be super specific, but should have some kind of discussion. Tools, theoretical discussion, good/bad values.

 [[KA5]](#_msoanchor_5)Differentiate between pre-training bias, and model biasMachine learning assumes that data can be used to train statistical models to pick up on patterns**. When patterns are unclear our models are at best useless, and at worst harmful.** Real-world data is messy, and signals can be hard to identify. Poor data quality greatly exacerbates this problem. State-of-the-art deep learning architecture may offer a marginal improvement in signal processing capability, but at the cost of increased computationally complexity and loss of explainability. The [data-centric AI](https://datacentricai.org/) movement was founded by Andrew Ng on the belief that better data is the next step to better AI.

**“The model and the code for many applications are basically a solved problem, Now that the models have advanced to a certain point, we got to make the data work as well.” - Andrew Ng**

              Data quality is a multidimensional issue ranging from simple validation to detecting intersectional biases. Many businesses are familiar with common sense pre-training data validation; what is referred to as **data quality.** Data quality and data-centric AI go beyond data quality and ask questions about the distribution of the dataset. **Data distribution quality** encompasses testing and validating the statistical assumptions made during pre-training, modeling, and deployment. **Data documentation** allows for all aspects of data and model quality to be communicated across silos reducing technical debt. This whitepaper focuses on **data quality for tabular**, but general principles are applicable to other datatypes as well.

## Data Quality

“Data Quality” contains most traditional aspects of data security. Is this data fundamentally correct? Creating & enforcing expectations for data quality are a key tool for data validation and data verification[[KA1]](#_msocom_1) .

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image002.jpg)

Data distribution quality is the focus of this document and refers to the statistical assumptions around the dataset and model. Data distribution quality can be broken down into 3 main components: 1) Pretraining, 2) Model Development, and 3) Deployment and monitoring. At each step the distributional qualities of the data must be assessed and validated in context. The following is a sample checklist of potential issues to consider. Every model may handle data differently, and its unique characteristics should be considered.

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image004.png)

Dataset and model documentation facilitate communication across silos and teams. A single project may need to communicate with multiple teams, and those teams may change over time. Standardized documents enforce a common language across the business to understand data science projects, use cases, and implementations. Current documentation standards are under development and include:

**Datasheets for Datasets[**[1]**](#_ftn1)**: The number of stake holders that need to understand a particular aspect of the data pipeline is large and everchanging. Datasheets help all stakeholders understand the data they are using. It also forces teams consider multiple aspects of their data. Areas covered include task motivation, dataset composition, data collection process, preprocessing/cleaning/labeling, data uses, dataset distribution, and maintenance.

**Model Cards[**[2]**](#_ftn2)**: Model cards standardize model documentation across use cases. This includes basic facts including which model(s) was used, how it was parametrized, performance, and evaluations for fairness.

# Data Quality Tools

**Great Expectations** [[KA2]](#_msocom_2) is a data quality tool created to enforce various constraints on a single or multiple columns of data. There is a large community developing expectations for rigorous statistical tests for tabular, geospatial, text, and image data.

Deequ[[3]](#_ftn3) is an open-source data quality software developed by amazon. PyDeequ[[4]](#_ftn4) is a python wrapper for Deequ. There are 3 main components to Deequ:

1.       **Metrics Computation** – Statistical metrics to measure the health and validity of your data. These can be as simple as mean, median, mode or as complicated as needed for assessing distributional qualities of your data.

2.       **Constraint Verification** – Validating the data that is being streamed into your applications to make sure it matches your expectations.

3.       **Constraint Suggestion** – Use automated constraint suggestion methods to profile your data and build expectations.

Deequ is implemented on top of **Apache Spark** and is designed to scale with large datasets that typically live in a distributed filesystem or a data warehouse.

Mislabeled data greatly impacts model performance and evaluations. Unfortunately, mislabeling is pervasive even in academic settings[[5]](#_ftn5). Manual label validation is labor intensive and infeasible in most contexts. [**CleanLab**](https://docs.cleanlab.ai/v2.0.0/index.html)[****[6]****](#_ftn6) provides a suite of tools for **finding and fixing potential label errors.** Better labels cut through confusing signals in training and validation data leading to better model performance. More accurate testing labels provide better model evaluation. The release of CleanLab 2.0 expands opportunities to productionalize label correction with just a few lines of code.

![9 examples label errors in the MNIST dataset](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image006.png)

Labelbox[[7]](#_ftn7) is an enterprise tool for active learning, data labeling, and annotation. Kimberly-Clark has access to Labelbox for improving text and image labels. Labelbox provides an end-to-end system for improving model performance. Improving labels, versioning data, and leveraging automation make Labelbox more than a simple data annotation app.

# Data Quality

To ensure data meets quality and governance guidelines, the guidelines must first be defined. Building expectations requires understanding the business task and goal. Once the ML task has been defined the data lineage should be cataloged. **Data lineage** [[KA3]](#_msocom_3) tracks the flow of data from data ingestion/creation all the way to model deployment. Every column should have its lineage tracked including all preprocessing tasks.

# Data Distribution Quality

Generic data quality constraints and expectations are a solid foundation to building good models, but every model may have different constraints and requirements. It’s important to choose the correct model for the task: interpolation or extrapolation? Is the quantity of quality data enough for this model? Are there additional constraints on data that the model enforces? i.e., no endogeneity, data following a certain distribution, etc. Testing for these assumptions will lead to better model selection, avoiding overfitting, and selecting a model with an appropriate level of interpretability.

Additional data-centric considerations include, but are not limited to:

·       What level of performance is required to move forward to deployment?

·       Has the model been stress-tested against out-of-sample behavior?

·       Has the model been stress-tested against spurious correlations?

·       Are there patterns in model underperformance?

·       Has the model been stress-tested against bias? (Models can in theory produce biased predications even with strong pre-training checks)

·       Can model performance be boosted with synthetic data or producing more labeled data?

·       What range should model predictions be in?

Stress-testing models produces robust predictions and can help prevent unwanted behaviors before they occur in the real world. Picking up on extreme behaviors or potential biases ensures that the model is equipped for the uncertainty in the real world.

## Data Distribution Distance Measures

Assessing model assumptions, measuring bias, and detecting data drift all rely on accurately being able to **detect the difference between two statistical distributions**. When the target distribution is known (i.e., assessing normality for a linear model) parametric statistical tests can be used. Oftentimes the underlying distribution of the data is unknown, or it is infeasible to build customized tests for ever column of the data. Nonparametric tests are uses in this case.

Kullbeck-Leibler Divergence, Population Stability Index, and Jensen-Shannon Divergence are **nonparametric tests for discrete random variables.**

Kolmogorov-Smirnov Test, Mann-Whitney U Test, and the Cucconi test are **nonparametric tests for continuous random variables.**

The Anderson-Darling Test, Jarque-Bera Test, and Shapiro-Wilk Test **are parametric tests for normality.**

While the above tests are by no means a comprehensive review, they provide a solid starting point for distributional measures. Each test has its strengths and limitations, and some applications may benefit from more careful applications of tests. In others general monitoring maybe sufficient. If unsure here are general recommendations for evaluation:

**Case**

**Test/Measure**

2 independent discrete random variables

Population Stability Index

2 independent continuous distributions

Kolmogorov-Smirnov Test

1 variable assessment of normality 

Shapiro-Wilk Test

###  

### Kullbeck-Leibler Divergence

Discrete random variables provide a much simpler methodology for measuring divergence. Kullbeck-Leibler divergence (or relative entropy) provide a simple measure of divergence between two probability distributions. KL divergence is also well defined for the parametric continuous case but breaks down in the nonparametric case. The formula for KL divergence is as follows in the discrete case.

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image008.png)

 In the continuous case we simply model this utilizing an integral. An important characteristic of KL divergence is that it is not symmetric. In general, this means that

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image010.png)

KL divergence can be implemented with SciPy: [scipy.special.rel_entr — SciPy v1.8.1 Manual](https://docs.scipy.org/doc/scipy/reference/generated/scipy.special.rel_entr.html#scipy.special.rel_entr). [[KA4]](#_msocom_4) Note that the scipy.special.kl_div is NOT the formula provided above, it adds two extra terms.

KL divergence is a measure of distance with 0 representing identical distributions, and larger values signaling larger divergences. KL divergence will always be non-negative, and there is no theoretical upper bound. It can be difficult to interpret and determine cut-offs for divergence based on KL divergence.

### Population Stability Index

We can consider the symmetric version of the KL divergence as

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image012.png)

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image014.png)

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image016.png)

This symmetrical KL divergence is known as the **Population Stability Index**. The PSI provides one key advantage of the KL Divergence which is a known distribution[[8]](#_ftn8). Through a Taylor series expansion, it can be shown that PSI approximately follows a chi-squared distribution which allows us to conduct the following hypothesis test:

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image018.png)

The null is rejected if

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image020.png)

Where n is the number of samples from P, m is the number of samples from Q, alpha is the probability of type 1 error, and B is the number of levels in the data.

### Jensen-Shannon Divergence

The Jensen-Shannon divergence (JS) measures how much the label distributions of different facets diverge from each other entropically. It is based on the Kullback-Leibler divergence, but it is symmetric.

The formula for the Jensen-Shannon divergence is as follows:

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image022.png)

The range of JS values for binary, multicategory, continuous outcomes is ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image024.png).

-   Values near zero mean the variables are similarly distributed.
-   Positive values mean the distributions diverge, the more positive the larger the divergence.

This metric indicates whether there is a big divergence in one of the labels across facets

### LP-Norm

The ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image026.png)-norm (LP) measures the p-norm distance between two distributions of a variable. This metric is non-negative and so cannot detect reverse bias.

The formula for the ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image026.png)-norm is as follows:

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image028.png)

The norm measures the distance between two vectors.

### Total Variation Distance

The total variation distance data bias metric (TVD) is half the L1-norm. The TVD is the largest possible difference between the probability distributions for label outcomes of facets _a_ and _d_. The L1-norm is the Hamming distance, a metric used compare two binary data strings by determining the minimum number of substitutions required to change one string into another. If the strings were to be copies of each other, it determines the number of errors that occurred when copying. In the bias detection context, TVD quantifies how many outcomes in facet _a_ would have to be changed to match the outcomes in facet _d_.

The formula for the Total variation distance is as follows:

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image030.png)

For example, assume you have an outcome distribution with three categories, ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image032.png) in a college admissions multicategory scenario. You take the differences between the counts of facets _a_ and _d_ for each outcome to calculate TVD. The result is as follows:

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image034.png)

Where:

-   ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image036.png) is number of the ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image038.png) category outcomes in facet _a_: for example na(0) is number of facet _a_ acceptances.
-   ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image040.png) is number of the ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image042.png) category outcomes in facet ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image044.png): for example, ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image046.png) is number of facet _d_ rejections.

The range of TVD values for binary, multicategory, and continuous outcomes is ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image048.png), where:

o   Values near zero mean the labels are similarly distributed.

o   Positive values mean the label distributions diverge, the more positive the larger the divergence.

### Kolmogorov-Smirnov Test

Continuous random variables may have unknown distributions which makes testing for data drift difficult. The branch of nonparametric statistics deals with the case where the underlying distribution of a test statistic is unknown. The Kolmogorov-Smirnov test is one such nonparametric test with simple intuition – measure the maximum difference between two empirical CDF’s (or between an empirical CDF and theoretical CDF).

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image050.png)

Figure 5 - Kolmogorov-Smirnov Test Illustration

The KS-Test is built to detect the difference in distribution between two continuous distributions based on their CDF's. This can be two unknown samples (2-sample KS-Test) or a single unknown variable and a target distribution (i.e. normal, exponential, etc.) The KS test statistic can be calculated with

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image052.png)

The KS test statistic follows the Kolmogorov distribution. To conduct a KS test, simply use the SciPy library. The KS test works at very low sample sizes but is not the most powerful test for detecting normality. In the case of normal distributions, standardize the data and calculate the KS test statistic with the standard normal distribution. For large sample sizes errors may propagate, but downsampling or kernel approximation may be appropriate. KS test statistic is well defined for discrete random variables, but for discrete RVs with few levels the KL divergence may be a more appropriate measure.

### 1.1.1.            Shapiro-Wilk Test

The Shapiro-Wilk test is the most powerful test for assessing normality. It tests the null hypothesis ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image054.png), that a sample ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image056.png)came from a normally distributed population. The Shapiro-Wilk Test statistic is

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image058.png)

The cutoff values and test statistic are typically computed using statistical software like SciPy.

### Class Imbalance

Class imbalance measures which classes have fewer training samples based on a characteristic. CI is important to track because models will preferentially fit the larger classes at the cost of the smaller ones. For a column of data with two values ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image060.png), ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image062.png) the CI can be calculated as ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image064.png)

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image066.png) will range from ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image068.png) with positive values representing facet ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image060.png) having more training samples, negative values indicating facet ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image062.png) has more examples.

### Label Imbalance

Label imbalance extends the idea of class imbalance to ratios of different labels. It measures the difference in proportions of labels (DPL) for an observed label ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image070.png) between two facets of a column. A machine learning model trained on this data will learn the relationship between the facets and the outcome resulting in bias. DPL can be calculated as follows.

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image072.png)

Where ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image074.png) is the number of members in facet a with given label ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image070.png). If DPL is close enough to 0 then we say that demographic parity has been achieved. For binary and multicategory labels the DPL values range from ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image076.png).

·      ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image078.png) indicates that facet a has a higher proportion of positive outcomes

·      ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image080.png) near 0 indicate a more equal proportion of positive outcomes between facets and a value of 0 indicates perfect demographic parity

·      ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image082.png) indicates that facet ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image062.png) has a higher proportion of positive outcomes when compared with facet ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image060.png)

# Detecting Bias [[KA5]](#_msocom_5) 

              Unintentional bias in AI is a negative externality on marginalized groups and a regulatory risk. Despite bureaucratic lag the number of AI-related lawsuits has greatly increased. George Washington University has developed a [preliminary list](https://blogs.gwu.edu/law-eti/ai-litigation-database/) of such lawsuits[[9]](#_ftn9). In _Weapons of Math Destruction[**[10]**](#_ftn10)_ Cathy O’Neill details many instances of AI algorithms gone wrong. The stakes are incredibly high – a single AI lawsuit can cost millions in litigation, settlements, and damages. **One lawsuit has the potential to erase the cumulative benefits from a dozen AI initiatives**.

              When models train on biased data they learn human biases. AI’s ability to scale perpetuates these harms with incredible speed. Steps must be taken to ensure our datasets are free from bias based on protected characteristics including but limited to race, gender, sexuality, and age. Reducing bias is the morally right thing to do, but also provides protection against lawsuits and regulation. Given KC’s multinational nature navigating unintentional bias is complex problem on the intersection of law and technology. Given this complex nature the following statistical techniques to detect bias are simply tools that must be applied carefully. When in doubt legal considerations should be voiced and evaluated on a case-by-case basis. 

## Overview on Detecting Bias

The first step in detecting bias is determining the column of the interest. This column typically describes protected characteristics like sex, gender, race, or sexuality. Other sources of bias can include nationality, region, or any other category. Bias in models can extend beyond protected characteristics and show up in unexpected places. Assessing against these spurious correlations is always a good idea.

When measuring pretraining bias the different categories of a given characteristic are known as **facets**. Most of measuring pretraining bias is assessing the distributional differences between these facets.

# Data Drift

Model deployment and monitoring is of utmost important to ensure that behavior is on track. Once out in the wild, model inputs and outputs must be carefully monitored. This includes data validation, limiting access, and safeguards against adversarial examples (if applicable).

Data drift is unexpected and undocumented changes to data structure, semantics, and/or distribution that is a result of modern data architectures. Data drift breaks processes and corrupts data but can also reveal new opportunities for data use. Oftentimes the distribution of data at time of training becomes obsolete by the time production is ready for data. As we stream new data checking for changes in the distribution of data is key to preventing performance failures in your machine learning pipeline.

## Overview of Data Drift

In supervised and semi-supervised settings, observations ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image084.png) are assumed to be drawn independently from the same joint distribution ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image086.png) If data begins to diverge from this distribution our model assumptions do not hold. This is data drift. Monitoring data drift is difficult because model assumptions can vary widely and, data can range from images, text, tabular, to complicated graph structures. Formally data drift occurs when the training distribution![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image088.png) and the real-world distribution, ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image090.png) diverge.

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image092.png)

Not only can data drift mess with overall distribution, it can also violate assumptions of independence if there are external factors changing the distribution, or drift occurs in a particular direction due to macroeconomic conditions. Some causes of drift to watch out for include:

1.       Sample selection bias

2.       Non-stationary environment

**Feature drift** occurs when the underlying distribution of the feature vectors change, but the ground truth relationship between ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image094.png) and ![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image096.png) remains the same. In simpler terms, data that previously was underrepresented (or not present) is observed more frequently. Formally feature drift (or covariate drift) occurs when

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image098.png)

**Concept drift** is the opposite of feature drift. The feature/covariate distributions remain the same, but the target distributions have changed. Formally concept drift occurs when

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image100.png)

**Dual drift** is when we have both feature drift and concept drift at the same time.

![](file:///C:/Users/U32312/AppData/Local/Temp/msohtmlclip1/01/clip_image102.png)

## Detecting Data Drift

Detecting data drift on tabular data involves monitoring the distribution of production data in comparison to the training data. These differences can be monitored by the various statistical tests presented in Section 4.1 – Distributional Distance Measures. Each column can be treated as unparametrized random variable, and the model can be retrained when significant drift is detected.

## Non-Tabular Data

Detecting data drift for non-tabular datatypes is still an emerging field with no clear answers. Current approaches hinge upon using low-dimensional embeddings as proxies for catching data drifts.

# Potential Future Directions

## Bayesian Nonparametric Methods

There are 4 primary branches in statistics stemming from a combination of bayesian vs. frequentist and parametric vs. nonparametric. Frequentist statistics are taught in school - confidence intervals, hypothesis tests with p-values, and other inference models assuming that the true nature of the world is a fixed quantity to determine from observation. Bayesians believe the world to be everchanging and update their beliefs about the quantity in question as more information (data) becomes available.

 Parametric statistics is concerned with the study of models with fixed parameter values that are to be determined. Nonparameterics in contrast assumes that there are an infinite number of possible parameters that can take on almost any value that cannot be precisely determined. Frequentist and bayesian parametric statistics assume that the underlying truth is a function of a certain quantities i.e. the mean and the variance of a normal distribution. In the nonparametric world we make no such assumptions about the underlying distribution. While this generalization makes things more difficult, it oftentimes more accurately reflects the uncertainty in distributional qualities that real world data exhibits.

Possible directions for concept drift detection come from bayesian nonparameterics including Dirichlet processes, Gaussian mixture models, and polya tree tests[[11]](#_ftn11).

  

---

[[1]](#_ftnref1) [Datasheets for Datasets](https://arxiv.org/abs/1803.09010) – Gebru et. al. 2021

[[2]](#_ftnref2) [Model Cards for Model Reporting](https://arxiv.org/abs/1810.03993) – Mitchell et. al. 2019

[[3]](#_ftnref3) [Test data quality at scale with Deequ | AWS Big Data Blog (amazon.com)](https://aws.amazon.com/blogs/big-data/test-data-quality-at-scale-with-deequ/)

[[4]](#_ftnref4) [PyDeequ GitHub](https://github.com/awslabs/python-deequ)

[_**[5]**_](#_ftnref5) [_Pervasive Label Errors in Test Sets Destabilize Machine Learning Benchmarks_](https://arxiv.org/abs/2103.14749)_,_ Northcutt et. al. 2021

[[6]](#_ftnref6) [Cleanlab](https://cleanlab.ai/)

[[7]](#_ftnref7) [Labelbox: the leading training data platform for production AI](https://labelbox.com/)

[[8]](#_ftnref8) [Statistical Properties of Population Stability Index](http://www.stat.wmich.edu/naranjo/PSI.pdf), Naranjo. 2018

[[9]](#_ftnref9) Ethical Tech Initiative of DC, Professor Robert Brauneis. 2021

[[10]](#_ftnref10) [Weapons of Math Destruction - Wikipedia](https://en.wikipedia.org/wiki/Weapons_of_Math_Destruction)

[[11]](#_ftnref11) [Bayesian Nonparametric Unsupervised Concept Drift Detection for Data Stream Mining | ACM Transactions on Intelligent Systems and Technology](https://dl.acm.org/doi/10.1145/3420034)

---
