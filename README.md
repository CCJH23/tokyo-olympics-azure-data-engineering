# Tokyo Olympics Azure Data Engineering Project
Data Engineering Project using Azure on Tokyo Olympics 2020


## Architecture Diagram
![Architecture Diagram](https://github.com/CCJH23/tokyo-olympics-azure-data-engineering/blob/73ff1272546af51d9cb12fc8093ab6bacfa2da0c/img/Tokyo%20Olympic%20Azure%20Data%20Eng%20Project%20Architecture.png)


## Kaggle Dataset
Link: [Tokyo Olympics 2020](https://www.kaggle.com/datasets/arjunprasadsarkhel/2021-olympics-in-tokyo)

## Data Visualisation
### Top Countries Medals Count
![Medals](https://github.com/CCJH23/tokyo-olympics-azure-data-engineering/blob/b31ea0c374a8711023d813389ffe54dfa143881b/img/Medals.png)

### Proportion of Males per Sport
![Proportion of Males Per Sport](https://github.com/CCJH23/tokyo-olympics-azure-data-engineering/blob/46e99b37919a4eae6196934d1b8c43c248a7937c/img/Proportion%20of%20Males%20Per%20Sport.png)

### Sports in terms of Popularity
![Total Number of Athletes per Sport](https://github.com/CCJH23/tokyo-olympics-azure-data-engineering/blob/46e99b37919a4eae6196934d1b8c43c248a7937c/img/Total%20Num%20Athletes%20Per%20Sport.png)


## Technologies used
1. Data Factory
    1. Create and manage data pipelines
2. Data Lake Gen 2
    1. Store structured or unstructured files
3. Azure Databricks
    1. For data exploration and data processing
4. Synapse Analytics
    1. Data warehouse to analyse and process data for BI and analytics
5. Tableau
    1. Data visualisation  


## Process
1. Create storage accounts
    1. Get storage account so that I can store files on Azure, specifically in the containers data storage
    2. Create 2 folders, raw-data and transformed-data

2. Data Source
    1. Get dataset from Kaggle
    2. Upload to Github
    3. Get the raw link of the dataset from Github

3. Data Ingestion
    1. Create data pipeline in Azure Data Factory
    2. To copy data from Github raw links and store in raw-data folder in data lake  

4. Data Transformation
    1. Create and deploy a Azure Databricks Workspace
    2. Create a compute where the Spark code will run on
    3. Write transformation code on Databricks notebook
        1. Connect Databricks to data lake so that you can access the data in the notebook and do transformations
        2. Create an app in App Registration to get client id, tenant id and secret id for Databricks to use to connect to the data lake
        3. Mount data lake to Databricks
        4. Give the app you created earlier the blob storage permission in the data lake for the app (Databricks) to access the data lake
        5. Read the datasets and cast the columns into proper format (e.g. int)
        6. Write and store the transformed data in transformed-data folder in data lake 

5. Data Analytics
    1. Create tables from the datasets in transformed-data folder in data lake
    2. Do data analytics using SQL
    3. Do data visualisation using Tableau
