# Python-Sklearn-Classifier-Pickle-Dash-PowerBI
This article shows you how to create a classification model with Python and Sklearn in Azure Databricks and save/load the model by using Pickle library.

## Problem Statement
We model the loan application as a two-class classification problem: Based the historical applications with a number of features, the application may approved or denied. Logistic Regression method is used in this exercise. 

After the LR model is trained based the historical dataset, we want to save the model for use in different time and location. Thus, the Pickle library is employed to do so.

> The pickle library implements a fundamental, but powerful algorithm for serializing and de-serializing a Python object structure. “Pickling” is the process whereby a Python object hierarchy is converted into a byte stream, and “unpickling” is the inverse operation, whereby a byte stream is converted back into an object hierarchy.

## Environment
We use Azure Data Lake Storage Gen 2 (ADLSG2) File System for storing all the files. Under project folder, there are three sub-folders:
- Input - dir for input file
- Output - dir for output file
- Model - dir pkl file

We use Azure Databricks with a cluster of version 6.0 (includes Apache Spark 2.4.3, Scala 2.11). Under project folder in Workspace, our python notebooks are saved in three sub folders: 
- train - the model training and saving
- score - the model loading and scoring
- test - reserved for unit tests

The ADLSG2 is mounted to the Azure Databricks workspace by following this document: https://docs.microsoft.com/en-us/azure/storage/blobs/data-lake-storage-use-databricks-spark

## Dataset
The dataset is from the example of "https://raw.githubusercontent.com/callxpert/datasets/master/Loan-applicant-details.csv". 

## Pickle Library
This library has been pre-installed in the Azure Databricks Python runtime. The code examples can be found in https://dataaspirant.com/2017/02/13/save-scikit-learn-models-with-python-pickle/

## Method
After the minimal data preprocessing, we use 80% of the dataset to train Sklearn LogisticRegression model. The training result is validated by the 20% fo remaining dataset with an accuracy of 0.7. Afterward the model is saved as pkl file in DBFS.

The model has been consumed by another notebook. In it we first load the pkl file, and then we use the whole dataset to run through the model to pretend regression test the model with an unseen dataset. This time we get an accuracy of 0.8.

The resulted dataset, aka, the original dataset with a new column, called predictions, is saved as a CSV file in DBFS. Also a permanent table is created based on the file for Power BI to use.

## Presentation
The results are presented by Power BI Desktop and Power BI web. At this moment, Power BI Desktop has a ADLSG2 connector, by using it, we created a pbix file and publish in powerBI.com. However, the connector is in Beta version and does not support refreshing. We heard that once the connector GA-ed, the refreshing will be supported.

The results are also presented in a Databricks Dashboard built on the top of a notebook. We can distribute the URL of of dashboard's presentation so everyone who has access to the Databricks worksppace will be able to run this dashboard which predict one loan application at a time by loading the model and scoring the user entry.



