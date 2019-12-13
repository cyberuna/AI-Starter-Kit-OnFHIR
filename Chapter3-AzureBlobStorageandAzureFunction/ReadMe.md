# Chapter 3 - Azure Blob Storage and Azure Function: Ingest data into Azure API for FHIR

## Azure Function
[Azure Functions](https://docs.microsoft.com/en-us/azure/azure-functions/) is a serverless compute service that lets you run event-triggered code without having to explicitly provision or manage infrastructure.

This Azure Function is created to monitor the storage account, and ingest any FHIR bundles uploaded to the container into the Azure API for FHIR service.


Deploy the function using the template [azuredeploy-importer.json](./azuredeploy-importer.json) using [Azure Resource Manager in Azure Portal](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-template-deploy-portal#deploy-resources-from-custom-template). This template will deploy an Azure Storage account, Application Insights and the Function in an Azure Container Instance. 

When deploying, the following environment variables should be set:

```
APPINSIGHTS_INSTRUMENTATIONKEY=<KEY>
Audience=<e.g. https://azurehealthcareapis.com>
Authority=<e.g. https://login.microsoftonline.com/TENANT-ID>
AzureWebJobsDashboard=<STORAGE ACCOUNT CONNECTION STRING>
AzureWebJobsStorage=<STORAGE ACCOUNT CONNECTION STRING>
ClientId=<CLIENT ID (service client)>
ClientSecret=<CLIENT SECRET>
FhirServerUrl=<e.g. https://myaccount.azurehealthcareapis.com>
MaxDegreeOfParallelism=<default 16>	
```

## Azure Blob Storage
Container `fhirimport` and `fhirrejected` will be created in the storage account.
When FHIR bundles are uploaded to `fhirimport` container, Azure Function gets triggered and data will be ingested into Azure API for FHIR service. If there are files that doesn't follow the FHIR standard, they will be moved into `fhirrejected` container. Once the files are ingested into the FHIR service, they will be removed from `fhirimport` container.

Containers azure-webjobs-hosts and azure-webjobs-secrets will be created for use by the app.

***

[Go to Chapter 4 - Azure Data Factory: Convert bundles to delimited json (ndjson)](../Chapter4-AzureDataFactory/ReadMe.md)
