# OnFHIR - Starter Kit for Azure API for FHIR 

#### This repository brings together the below Github repos and reference architecture(s) demonstrating integration capabilities of [Azure API for FHIR](https://docs.microsoft.com/azure/healthcare-apis). 

   * [Synthea](https://github.com/synthetichealth/synthea)
   * [FHIR Server Samples](https://github.com/microsoft/fhir-server-samples)
   * [Health Architectures](https://github.com/microsoft/health-architectures)
   * [DICOM Server](https://github.com/microsoft/dicom-server)
   * [OpenHack FHIR](https://github.com/microsoft/OpenHack-FHIR)

# Prerequisites
Azure Subscription is required to complete this starter kit. Azure Subscription can be created for [free](https://azure.microsoft.com/en-us/free/)

# Reference Architectures
<center><img src="images//azure-api-fhir-paas.png" width="850"></center>

Reference architecture includes: 
#### * [Chapter01 - Generate Data: Generate FHIR data using Synthea](./Chapter01-GenerateData/ReadMe.md)
#### * [Chapter02 - Ingest and Store Data: Upload the generated data into Azure Blob Storage. Ingest into Azure API for FHIR using an Azure Function](./Chapter02-IngestandStoreData/ReadMe.md)
#### * [Chapter03 - Export and Anonymize Data: Export FHIR data using Logic Apps into Blob Storage. Anonymize and store into Azure Data Lake Storage](./Chapter03-ExportandAnonymizeData/ReadMe.md)
#### * [Chapter04 - HL7 Ingest and Convert: Ingest HL7v2 messages and convert to FHIR](./Chapter04-HL7IngestandConvert/ReadMe.md)
#### * [Chapter05 - IoT FHIR Connector: Ingest data from IoT Central devices and persist in a FHIR® server](./Chapter05-IoTFHIRConnector/ReadMe.md)
#### * [Chapter06 - Healthcare Bot: Appointment Scheduler allow users to schedule an appointment and Back to Work is COVID-19 symptom screening for employees to return to work](./Chapter06-HealthcareBot/ReadMe.md)
#### * [Chapter07 - Analyze and Visualize Data: Prepare data using Azure Databricks, store in Azure SQL DB and analyze using PowerBI](./Chapter07-AnalyzeandVisualizeData/ReadMe.md)
#### * [Chapter08 - Open Source FHIR Server: Setup and Configure open source FHIR server](./Chapter08-OpenSourceFHIRServer/ReadMe.md)
#### * [Chapter09 - DICOM Server: Deploy Medical Imaging Server for DICOM and ingest metadata into FHIR server](./Chapter09-DICOM/ReadMe.md)
#### * [Chapter10 - Text Analytics for Health: Deploy in containers and test using web app](./Chapter10-TextAnalytics/ReadMe.md)


# Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us the rights to use your contribution. For details, visit https://cla.microsoft.com.

When you submit a pull request, a CLA-bot will automatically determine whether you need to provide a CLA and decorate the PR appropriately (e.g., label, comment). Simply follow the instructions provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

# Disclaimer 

This sample is provided as-is and is not meant for use in a production environment. It is provided only for illustrative purposes. The end user must test and modify the sample to suit their target environment. 

Microsoft can make no representation concerning the content of this sample. Microsoft is providing this information only as a convenience to you. This is to inform you that Microsoft has not tested the sample and therefore cannot make any representations regarding the quality, safety, or suitability of any code or information found here.   

***

[Home](https://github.com/cyberuna/AI-Starter-Kit-OnFHIR)
