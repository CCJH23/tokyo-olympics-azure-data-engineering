# Tokyo Olympics Azure Data Engineering Project
Data Engineering Project using Azure on Tokyo Olympics 2020

This README describes the architecture of the project and how it is done.

## Architecture Diagram
![Architecture Diagram](https://github.com/CCJH23/tokyo-olympics-azure-data-engineering/blob/73ff1272546af51d9cb12fc8093ab6bacfa2da0c/img/Tokyo%20Olympic%20Azure%20Data%20Eng%20Project%20Architecture.png)

## Kaggle Dataset
Link: [Tokyo Olympics 2020](https://www.kaggle.com/datasets/arjunprasadsarkhel/2021-olympics-in-tokyo)

## Technologies used
1. Data Factory
    1. Create and manage data pipelines
2. Data Lake Gen 2
    1. Store structured or unstructured files
3. Azure Databricks
    1. For data exploration and data processing
4. Synapse Analytics
    1. Data warehouse to analyse and process data for BI and analytics

## Process
1. Create storage accounts
- Get storage account so that I can store files on Azure, specifically in the containers data storage
- Create 2 folders, raw-data and transformed-data

2. Data Source
- Get dataset from Kaggle
- Upload to Github
- Get the raw link of the dataset from Github

3. Data Ingestion
- Create data pipeline in Azure Data Factory
- To copy data from Github raw links and store in raw-data folder in data lake  

4. Data Transformation
- Create and deploy a Azure Databricks Workspace
- Create a compute where the Spark code will run on
- Write transformation code on Databricks notebook
    - Connect Databricks to data lake so that you can access the data in the notebook and do transformations
        - Create an app in App Registration to get client id, tenant id and secret id for Databricks to use to connect to the data lake
        - Mount data lake to Databricks
        - Give the app you created earlier the blob storage permission in the data lake for the app (Databricks) to access the data lake
    - Read the datasets and cast the columns into proper format (e.g. int)
    - Write and store the transformed data in transformed-data folder in data lake 

5. Data Analytics
- Create tables from the datasets in transformed-data folder in data lake
- Do data analytics using SQL
