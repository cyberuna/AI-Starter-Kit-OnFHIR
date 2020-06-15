# Chapter 4 - Azure Data Factory: Convert bundles to delimited json (ndjson)

#### This chapter shows how to setup Azure Data Factory and convert json files to delimited json files.

## Prerequisites
* Knowledge of [Azure Data Factory](https://docs.microsoft.com/en-us/azure/data-factory/introduction)

Azure Data Factory is a cloud data integration service that orchestrates and automates movement and transformation of data.
This Data Factory is used to export resource types to [ndjson](http://ndjson.org/) files. 

## Steps
* Setup:\
-- Creata a [Azure Data Factory resource](https://docs.microsoft.com/en-us/azure/data-factory/quickstart-create-data-factory-portal) in Azure.\
-- Create a [Azure Blob Storage](https://docs.microsoft.com/en-us/azure/storage/blobs/storage-quickstart-blobs-portal) with 2 containers `datastaging` and `dataexport`.\
-- Download the [template](./azuredeploy-adf.json).\
-- Go to Azure Portal and search for "Deploy a custom template". Click "Build your own template in the editor" and Load the template from the above step. Click Save.\
<center><img src="../images/adf-deploytemplate.PNG" width="500"></center>
-- Enter the details for parameters and Click Create.\
```
   Choose the Subscription
   Choose or Create new Resource group
   Choose a Region
   Enter the name of the Azure Data Factory
   Enter the Azure API for FHIR URL
   Enter the Azure API for FHIR Client ID
   Enter the Azure API for FHIR Client Secret
   Enter the Azure tenant ID
   Enter the Azure API for FHIR URL
   Change the next 4 parameters if needed
   Enter the Azure Blob Storage connection string
```
* Validation & Run:\
-- Open the Azure Data Factory just created, and Click Author and Monitor.\
-- 2 Linked Services, 3 Datasets and 1 Pipeline will be created.
<center><img src="../images/adf-linkedservices.PNG" width="200"></center> <center><img src="../images/adf-datasets.PNG" width="200"></center> <center><img src="../images/adf-pipeline.PNG" width="200"></center>
-- Click Debug or trigger to run the Pipeline.\ 
-- Patient.json file will be created in `datastaging` and `dataexport` containers.\
-- Create Datasets and Pipelines as needed for other FHIR resources.\

***

[Go to Chapter 5 - Azure Databricks: Parse json and load into Azure SQL DB](../Chapter5-AzureDatabricks/ReadMe.md)
