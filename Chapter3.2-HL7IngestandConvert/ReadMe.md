# Chapter 3.1 - HL7 Ingest and Convert: Ingest HL7v2 messages and convert to FHIR

#### This chapter is sub-version of [HL7Conversion](https://github.com/microsoft/health-architectures/tree/master/HL7Conversion). Download/Clone this [repo](https://github.com/microsoft/health-architectures).

This chapter focuses on ingesting a sample ADT01 HL7v2 message into Azure API for FHIR.

## Prerequisites
* [Azure API for FHIR R4 server](../Chapter2-AzureAPIforFHIR/ReadMe.md).

## Steps
1. Download/Clone this [repo](https://github.com/microsoft/health-architectures).
2. [Deploy  HL7 Ingest Platform](https://github.com/microsoft/health-architectures/tree/master/HL7Conversion#deploying-your-own-hl7-ingest-platform).
3. Deploy HL7toFHIR Conversion Workflow.
For [reference](https://github.com/microsoft/health-architectures/tree/master/HL7Conversion#-deploying-your-own-hl7tofhir-conversion-workflow).
4. Collect the following information from "Azure API for FHIR" created in [Chapter2](../Chapter2-AzureAPIforFHIR/ReadMe.md)
   + Client/Application ID for the Client App
   + The Client Secret for the Client App
   + The AAD Tenant ID for the FHIR Server/Client App
   + The Audience/Resource for the FHIR Server/Client App typically https://myfhirazurehealthcareapis.com for Azure API for FHIR
5. Collect the following information from step2, the HL7 Ingest platform deployment (provided at the end of your deployment):
   + The resource group name created
   + The storage account name created
   + The service bus namespace created
   + The service bus destination queue name created
6. Open a shell or command window into the Azure CLI 2.0 environment
7. Run the deployhl72fhir.bash script and follow the prompts
8. After successful deployment your converter pipeline is now tied to your ingest platform from above.  To test, run the below with the sample HL7 message downloaded/Cloned from the Git in Step1 and resources will be created in the destination FHIR Server.
      ```
        curl --trace-ascii - -H "Content-Type:text/plain" --data-binary @samplemsg.hl7 <your ingest host name from above>/api/hl7ingest?code=<your ingest host key from above>
      ``` 
## Tips:
   + If Logic App is failing at step "ConvertHL7WithTemplate" with app timeout error, continue reading. When deploying HL7Conversion flow using deployhl72fhir.bash, the App Service will deploy a P1v2 SKU. If your subscription doesn't have availability for Premium, you will get an error. Changing it to Standard S1 SKU will work.
   + If Logic App is failing at step "ImportBundletoFHIR" with MethodNotFound error, continue reading. Go to Azure Portal, to the App Service in the target resource group created using deployhl72fhir. Click configuration and copy the API Key in CONVERSION_API_KEYS. Click overview and open the URL https://...azurewebsites.net, and paste the API Key in the popup and save. Click Load Template and choose ADT_A01.hbs. In the lower left window where the template has opened, change the type from transaction to batch. Azure API for FHIR doesn't support transaction as of now. Click Save. Re-run the Logic App that failed.
   + The resources are inserted into the FHIR server every time the Logic App is ran. To change to update, double-click on Patient in the template, scroll all the way to the bottom of the template, change the method from POST to PUT. To have the resource be used the reference ID, change the url to resource?_id={{ID}} where resource is Patient in this case. Repeat the same for all resources.
   + If the .hl7 file you are trying to convert doesn't have out of the box template, check this [Git](https://github.com/microsoft/FHIR-Converter) on how to create new templates.


*** 


