# Python-Sklearn-Classifier-Pickle
This article shows you how to create a classification model with Python and Sklearn in Azure Databricks and save/load the model by using Pickle library.

## Environment
We use Azure Data Lake Storage Gen 2 (ADLSG2) File System for storing all the files. Under project folder, there are three sub-folders:
- Input - dir for input file
- Output - dir for output file
- Model - dir pkl file

We use Azure Databricks with a cluster of version 6.0 (includes Apache Spark 2.4.3, Scala 2.11). Under project folder in Workspace, our python notebooks are saved in three sub folders: 
- train - the model training and saving
- score - the model loading and scoring
- test - reserved for unit tests

The ADLSG2 is mounted to the Azure Databricks workspace.

## Dataset
The dataset is from the example of "https://raw.githubusercontent.com/callxpert/datasets/master/Loan-applicant-details.csv". 

## Pickle Library
This libaray has been pre-installed in the Azure Databricks Python runtime. The code examples can be found in https://dataaspirant.com/2017/02/13/save-scikit-learn-models-with-python-pickle/



