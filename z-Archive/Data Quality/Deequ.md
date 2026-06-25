# Amazon Deequ 
Webpage: [[Test data quality at scale with Deequ | AWS Big Data Blog (amazon.com)](https://aws.amazon.com/blogs/big-data/test-data-quality-at-scale-with-deequ/)

Deequ is an open source amazon software for validating data quality. You generally write unit tests for your code, but do you also test your data? Incorrect or malformed data can have a large impact on production systems. Examples of data quality issues are:

-   Missing values can lead to failures in production system that require non-null values (NullPointerException).
-   Changes in the distribution of data can lead to unexpected outputs of machine learning models.
-   Aggregations of incorrect data can lead to wrong business decisions.

In this blog post, we introduce Deequ, an open source tool developed and used at Amazon. Deequ allows you to calculate data quality metrics on your dataset, define and verify data quality constraints, and be informed about changes in the data distribution. Instead of implementing checks and verification algorithms on your own, you can focus on describing how your data should look. Deequ supports you by suggesting checks for you. Deequ is implemented on top of [Apache Spark](https://spark.apache.org/) and is designed to scale with large datasets (think billions of rows) that typically live in a distributed filesystem or a data warehouse.

To use Deequ, let’s look at its main components (also shown in Figure 1).

-   **Metrics Computation** — Deequ computes data quality metrics, that is, statistics such as completeness, maximum, or correlation. Deequ uses Spark to read from sources such as Amazon S3, and to compute metrics through an optimized set of aggregation queries. You have direct access to the raw metrics computed on the data.
-   **Constraint Verification** — As a user, you focus on defining a set of data quality constraints to be verified. Deequ takes care of deriving the required set of metrics to be computed on the data. Deequ generates a data quality report, which contains the result of the constraint verification.
-   **Constraint Suggestion** — You can choose to define your own custom data quality constraints, or use the automated constraint suggestion methods that profile the data to infer useful constraints.

![Data Quality Constraints](https://d2908q01vomqb2.cloudfront.net/b6692ea5df920cad691c20319a6fffd7a4a766b8/2019/05/10/DataDeequ1.png)
## PyDeequ
PyDeequ is a wrapper for deequ. Let’s look at PyDeequ’s main components, and how they relate to Deequ (shown in the following diagram):

-   **Metrics computation** – Deequ computes data quality metrics, that is, statistics such as completeness, maximum, or correlation. Deequ uses Spark to read from sources such as [Amazon Simple Storage Service](http://aws.amazon.com/s3) (Amazon S3) and compute metrics through an optimized set of aggregation queries. You have direct access to the raw metrics computed on the data.
-   **Constraint verification** – As a user, you focus on defining a set of data quality constraints to be verified. Deequ takes care of deriving the required set of metrics to be computed on the data. Deequ generates a data quality report, which contains the result of the constraint verification.
-   **Constraint suggestion** – You can choose to define your own custom data quality constraints or use the automated constraint suggestion methods that profile the data to infer useful constraints.
-   **Python wrappers** – You can call each Deequ function using Python syntax. The wrappers translate the commands to the underlying Deequ calls and return their response.
![[PyDeequ Architecture.png]]
PyDeequ is built on top of Apache spark 

