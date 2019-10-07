# Python-Sklearn-Classifier-Pickle
This article shows you how to create a classification model with Python and Sklearn in Azure Databricks and save/load the model by using Pickle library.

## Environment
We use Azure Data Lake Storage Gen 2 (ADLSG2) File System for storing all the files in a hiarchial structure:
- POC
-- Input - dir for input file
-- Output - dir for output file
-- Model - dir pkl file

We use Azure Databricks with a cluster of version
6.0 (includes Apache Spark 2.4.3, Scala 2.11)

Our python notebooks are structured as
1. Project
1.1 train
1.2 score
1.3 test
