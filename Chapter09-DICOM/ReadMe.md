# Chapter 09 - DICOM Server

#### This chapter is sub-version of [DICOM Server](https://github.com/microsoft/dicom-server) focusing on setting up DICOM and DICOM Cast. 

The Medical Imaging Server for DICOM is an open source DICOM server that is easily deployed on Azure. It allows standards-based communication with any DICOMweb&trade; enabled systems, and injects DICOM metadata into a FHIR server to create a holistic view of patient data. The Medical Imaging Server for DICOM integrates tightly with the [Azure API for FHIR](https://docs.microsoft.com/azure/healthcare-apis/) enabling healthcare professionals, ISVs, and medical device vendors to create new and innovative solutions. FHIR is becoming an important standard for clinical data and provides extensibility to support integration of other types of data directly, or through references. By using the Medical Imaging Server for DICOM, organizations can store references to imaging data in FHIR and enable queries across clinical and imaging datasets.

The Medical Imaging Server for DICOM is a .NET Core implementation of DICOMweb&trade;. [DICOMweb&trade;](https://www.dicomstandard.org/dicomweb) is the DICOM Standard for web-based medical imaging. Details of our conformance to the standard can be found in our [Conformance Statement](docs/resources/conformance-statement.md).

## Setup
* Medical Imaging Server for DICOM Server
   * Deploy [Medical Imaging Server for DICOM](https://github.com/microsoft/dicom-server/blob/master/docs/quickstarts/deploy-via-azure.md) using ARM template.
   * Configure [Medical Imaging Server Server](https://github.com/microsoft/dicom-server/blob/master/docs/how-to-guides/configure-dicom-server-settings.md) if any changes needed from default.
   * Enable Authentication
      * Create [Resource Application](https://github.com/microsoft/dicom-server/blob/master/docs/how-to-guides/enable-authentication-with-tokens.md#create-a-resource-application-in-azure-ad-for-your-medical-imaging-server-for-dicom)
      * Create [Service Client Application](https://github.com/microsoft/dicom-server/blob/master/docs/how-to-guides/enable-authentication-with-tokens.md#create-a-service-client-application)
      * Set [Authentication](https://github.com/microsoft/dicom-server/blob/master/docs/how-to-guides/enable-authentication-with-tokens.md#set-the-authentication-of-your-app-service) in App Service.
      * Test Access in [Postman](https://github.com/microsoft/dicom-server/blob/master/docs/how-to-guides/enable-authentication-with-tokens.md#get-access-token-using-postman).
      * More on [Authentication](https://github.com/microsoft/dicom-server/blob/master/docs/how-to-guides/enable-authentication-with-tokens.md)

* FHIR
   * DICOM Cast currently only supports [FHIR OSS](https://github.com/microsoft/fhir-server/blob/master/docs/QuickstartDeployPortal.md).
   * Enable Authentication. These links are for DICOM, follow the same for FHIR OSS.
      * Create [Resource Application](https://github.com/microsoft/dicom-server/blob/master/docs/how-to-guides/enable-authentication-with-tokens.md#create-a-resource-application-in-azure-ad-for-your-medical-imaging-server-for-dicom)
      * Create [Service Client Application](https://github.com/microsoft/dicom-server/blob/master/docs/how-to-guides/enable-authentication-with-tokens.md#create-a-service-client-application)
      * Set [Authentication](https://github.com/microsoft/dicom-server/blob/master/docs/how-to-guides/enable-authentication-with-tokens.md#set-the-authentication-of-your-app-service) in App Service.
      * Test Access in [Postman](https://github.com/microsoft/dicom-server/blob/master/docs/how-to-guides/enable-authentication-with-tokens.md#get-access-token-using-postman).
      * More on [Authentication](https://github.com/microsoft/dicom-server/blob/master/docs/how-to-guides/enable-authentication-with-tokens.md)
   * Support for [Azure API for FHIR](https://docs.microsoft.com/en-us/azure/healthcare-apis/fhir-paas-portal-quickstart) is in the roadmap

* DICOM Cast
   * Deploy [DICOM Cast](https://github.com/microsoft/dicom-server/blob/master/docs/quickstarts/deploy-dicom-cast.md)
   * Authentication
      * Update [KeyVault Policy](https://github.com/microsoft/dicom-server/blob/master/docs/how-to-guides/sync-dicom-metadata-to-fhir.md#update-key-vault-for-dicom-cast)
      * Add [KeyVault Secrets](https://github.com/microsoft/dicom-server/blob/master/docs/quickstarts/deploy-dicom-cast.md#authentication).
   * Restart [DICOM Cast](https://github.com/microsoft/dicom-server/blob/master/docs/how-to-guides/sync-dicom-metadata-to-fhir.md#restart-azure-container-instance-for-dicom-cast)

* Store, Retrieve, Search, Delete DICOM data
   * [DICOMweb™ Standard APIs](https://github.com/microsoft/dicom-server/blob/master/docs/tutorials/use-the-medical-imaging-server-apis.md) with the Medical Imaging Server for DICOM
   * [DICOM Web Electron](https://github.com/microsoft/dicom-server/tree/master/tools/dicom-web-electron)
      * Change [Server Settings](https://github.com/microsoft/dicom-server/tree/master/tools/dicom-web-electron#getting-started)
      * Upload [Files](https://github.com/microsoft/dicom-server/tree/master/tools/dicom-web-electron#upload-dicom-files-to-your-server)
   * [Postman](https://github.com/microsoft/dicom-server/blob/master/docs/resources/Conformance-as-Postman.postman_collection.json)

* NOTE:
   * DICOM Web Electron doesn't work if DICOM Security is enabled.
   * Security Settings in KeyVault for DICOM Cast should match the Security Settings in App Settings Configuration for DICOM and FHIR OSS.
   * Restart the App Service if any configuration changes.
   * Restart the Azure Container Instance for DICOM Cast after any configuration changes in DICOM and FHIR OSS App configurations.
   * Re-deploy DICOM Cast if there are changes to App Service URL, as that is provided when creating using ARM Template.

*** 

[Home](https://github.com/cyberuna/AI-Starter-Kit-OnFHIR)
