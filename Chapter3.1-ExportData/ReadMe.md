# Chapter 3.1 - Export Data: Export FHIR data to Blob Storage

#### This chapter is sub-version of [FHIRExportQuickstart](https://github.com/microsoft/health-architectures/tree/master/FHIR/FHIRExportQuickstart) focusing on exporting data out of Azure API for FHIR. Click on the link for more details.

This chapter focuses on how to use Logic App to export FHIR data into Blob Storage as ndjson files.

## Prerequisites
* [Azure API for FHIR R4 server](../Chapter2-AzureAPIforFHIR/ReadMe.md).
* Knowledge of [Azure Blob Storage](https://docs.microsoft.com/en-us/azure/storage/blobs/storage-blobs-introduction)
* Knowledge of [Azure Logic Apps](https://docs.microsoft.com/en-us/azure/logic-apps/)
* Configured [Export for API for FHIR](https://docs.microsoft.com/en-us/azure/healthcare-apis/configure-export-data)

## Steps
* Setup:\
-- Copy [arm_template](./arm_template.json) and [arm_template_parameters](arm_template_parameters.json) to a folder.\
-- Open arm_template_parameters and update values for apiforfhir, tenantID, clientID, clientSecret.\
-- Open arm_template and update value for logicappname if you like to change the default name "fhirexport".\
-- Run the below using PowerShell to create Logic App that will be used to export FHIR data into Blob Storage.
```
   Connect to Azure: Connect-AzAccount
   Get the subscription ID: Get-AzSubscription
   Select the subscription, replace with your subscrption ID: Select-AzSubscription -SubscriptionId "<subscriptionID>"
   Create Logic App using ARM template, replace with your resource group: New-AzResourceGroupDeployment -ResourceGroupName "<resourcegroup>" -TemplateFile "./arm_template.json" -TemplateParameterFile "./arm_template_parameters.json"
```
* Validation & Run:\
-- Open Azure Portal and check if the Logic App is created.\
-- Manually trigger Logic App from Portal or use the command below.
```
Start-AzLogicApp 
     -ResourceGroupName <Name of resource group from above> 
     -Name <Name of logic app from above>
     -TriggerName "Recurrence"
```
-- Check the Blob Storage container which was configured in pre-requistes for ndjson files exported from FHIR server.\
-- You can also use GET in Postman using "https://<myfhir>.azurehealthcareapis.com/$export".\
-- Exporting individual resources like "https://<myfhir>.azurehealthcareapis.com/Patient/$export" is not supported yet.


*** 


