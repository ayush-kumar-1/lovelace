# Detect Pretraining Data Bias

[PDF](https://docs.aws.amazon.com/sagemaker/latest/dg/sagemaker-dg.pdf#clarify-detect-data-bias)[RSS](https://docs.aws.amazon.com/sagemaker/latest/dg/amazon-sagemaker-release-notes.rss)

Algorithmic bias, discrimination, fairness, and related topics have been studied across disciplines such as law, policy, and computer science. A computer system might be considered biased if it discriminates against certain individuals or groups of individuals. The machine learning models powering these applications learn from data and this data could reflect disparities or other inherent biases. For example, the training data may not have sufficient representation of various demographic groups or may contain biased labels. The machine learning models trained on datasets that exhibit these biases could end up learning them and then reproduce or even exacerbate those biases in their predictions. The field of machine learning provides an opportunity to address biases by detecting them and measuring them at each stage of the ML lifecycle. You can use Amazon SageMaker Clarify to determine whether data used for training models encodes any bias

Bias can be measured before training and after training, and monitored against baselines after deploying models to endpoints for inference. Pretraining bias metrics are designed to detect and measure bias in the raw data before it is used to train a model. The metrics used are model-agnostic because they do not depend on any model outputs. However, there are different concepts of fairness that require distinct measures of bias. Amazon SageMaker Clarify provides bias metrics to quantify various fairness criteria.

For additional information about bias metrics, see [Fairness Measures for Machine Learning in Finance](https://pages.awscloud.com/rs/112-TZM-766/images/Fairness.Measures.for.Machine.Learning.in.Finance.pdf).

## Amazon SageMaker Clarify Terms for Bias and Fairness

SageMaker Clarify uses the following terminology to discuss bias and fairness.

**Feature**

An individual measurable property or characteristic of a phenomenon being observed, contained in a column for tabular data.

**Label**

Feature that is the target for training a machine learning model. Referred to as the _observed label_ or _observed outcome_.

**Predicted label**

The label as predicted by the model. Also referred to as the _predicted outcome_.

**Sample**

An observed entity described by feature values and label value, contained in a row for tabular data.

**Dataset**

A collection of samples.

**Bias**

An imbalance in the training data or the prediction behavior of the model across different groups, such as age or income bracket. Biases can result from the data or algorithm used to train your model. For instance, if an ML model is trained primarily on data from middle-aged individuals, it may be less accurate when making predictions involving younger and older people.

**Bias metric**

A function that returns numerical values indicating the level of a potential bias.

**Bias report**

A collection of bias metrics for a given dataset, or a combination of a dataset and a model.

**Positive label values**

Label values that are favorable to a demographic group observed in a sample. In other words, designates a sample as having a _positive result_.

**Negative label values**

Label values that are unfavorable to a demographic group observed in a sample. In other words, designates a sample as having a _negative result_.

**Group variable**

Categorical column of the dataset that is used to form subgroups for the measurement of Conditional Demographic Disparity (CDD). Required only for this metric with regards to Simpson’s paradox.

**Facet**

A column or feature that contains the attributes with respect to which bias is measured.

**Facet value**

The feature values of attributes that bias might favor or disfavor.

**Predicted probability**

The probability, as predicted by the model, of a sample having a positive or negative outcome.

## Sample Notebooks

Amazon SageMaker Clarify provides the following sample notebook for bias detection:

-   [Explainability and bias detection with Amazon SageMaker Clarify](https://sagemaker-examples.readthedocs.io/en/latest/sagemaker_processing/fairness_and_explainability/fairness_and_explainability.html) – Use SageMaker Clarify to create a processing job for the detecting bias and explaining model predictions with feature attributions.

This notebook has been verified to run in Amazon SageMaker Studio only. If you need instructions on how to open a notebook in Amazon SageMaker Studio, see [Create or Open an Amazon SageMaker Studio Notebook](https://docs.aws.amazon.com/sagemaker/latest/dg/notebooks-create-open.html). If you're prompted to choose a kernel, choose **Python 3 (Data Science)**.

**Topics**

-   [Measure Pretraining Bias](https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-measure-data-bias.html)
-   [Generate Reports for Bias in Pretraining Data in SageMaker Studio](https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-data-bias-reports-ui.html)