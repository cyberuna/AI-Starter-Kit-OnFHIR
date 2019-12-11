# Chapter 2 - Azure API for FHIR: Create and configure

[FHIR](https://hl7.org/fhir/) standard is a new schema for US Healthcare that enables universal interoperability of EHR. FHIR ensures that data is stored in a consistent format   and uses unique identifiers to connect it to related patient data so that it is organized into structured data points.

[Azure API for FHIR](https://docs.microsoft.com/en-us/azure/healthcare-apis/) is a managed, standards-based, compliant API for clinical health data that enables solutions for actionable analytics and machine learning.
The Azure API for FHIR ingests, normalizes, secures and stores data with auditing and access controls.  Data can then be easily connected together and shared.

* [Setup Azure API for FHIR](https://docs.microsoft.com/en-us/azure/healthcare-apis/fhir-paas-portal-quickstart) to deploy FHIR service using the Azure portal.
* [Verify access to Azure API for FHIR with Postman](https://docs.microsoft.com/en-us/azure/healthcare-apis/access-fhir-postman-tutorial). Postman helps interact directly with the FHIR server as you build applications for debugging purposes.
* [Register Applications](https://docs.microsoft.com/en-us/azure/healthcare-apis/tutorial-1-decision-flow) shows the decision flow for Azure API for FHIR.
* Register Client Application: A client application registration is an Azure Active Directory representation of an application that can be used to authenticate on behalf of a user and request access to resource applications. A confidential client application is an application that can be trusted to hold a secret and present that secret when requesting access tokens.
  Register a [Confidential](https://docs.microsoft.com/en-us/azure/healthcare-apis/register-confidential-azure-ad-client-app) AND/OR [Public](https://docs.microsoft.com/en-us/azure/healthcare-apis/register-public-azure-ad-client-app) Application.
* Object IDs: The fully managed Azure API for FHIR service is configured to allow access for only a pre-defined list of identity object IDs. An identity object ID is either the object ID of a user or a service principal in Azure Active Directory. Object ID of the user creating the service is added by default. Add the [object ID](https://docs.microsoft.com/en-us/azure/healthcare-apis/find-identity-object-ids) for the client application to the FHIR service.
* Configure [Cosmos Database Settings](https://docs.microsoft.com/en-us/azure/healthcare-apis/configure-database). Azure API for FHIR uses Cosmos DB to store its data. Performance of the underlying database depends on the number of Request Units (RU) selected during service provisioning or in database settings after the service has been provisioned. Default is 400 RUs. This can be increased in Azure API for FHIR configuration. 
* [Enable Diagnostics Logging](https://docs.microsoft.com/en-us/azure/healthcare-apis/enable-diagnostic-logging) helps to monitor the service and provides compliance reports.


***

[Go to Chapter 3 - Azure Blob Storage and Azure Function: Bulk Ingest data into Azure API for FHIR](../Chapter3-AzureBlobStorageandAzureFunction/AzureFunction.md)
