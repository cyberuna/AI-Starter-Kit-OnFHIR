# Chapter11 - Power Platform

#### This chapter focuses on Power Platform connectors for Azure API for FHIR [FHIRBase](https://docs.microsoft.com/en-us/connectors/fhirbase/) and [FHIRClinical](https://docs.microsoft.com/en-us/connectors/fhirclinical/). 

A connector is a proxy or a wrapper around an API that allows the underlying service to talk to Microsoft Power Platform. Connectors provide a way for users to leverage a set of pre-built actions and triggers to build applications and workflows.

The two Connectors that works with Azure API for FHIR contain a subset of FHIR Resources and are bi-directional supporting both reads and writes to the FHIR Service. 

**[FHIRBase](https://docs.microsoft.com/en-us/connectors/fhirbase/)** and **[FHIRClinical](
https://docs.microsoft.com/en-us/connectors/fhirclinical/)** are certified custom connectors that allows for building secure healthcare applications to enable interoperability using FHIR.


## Use Power Platform Connectors Preview

The below steps are detailed in [FHIRPower](https://github.com/microsoft/FHIRPower).

   * Deploy Azure API for FHIR with First Party Auth. Add users to `FHIR Data Reader` or `FHIR Data Contributor` role using Access Control (IAM). Load sample data into Azure API for FHIR.
   * Deploy FHIRBase and FHIRClinical connectors to Power Platform environment.
   * Import samples and test.

*** 

[Home](https://github.com/cyberuna/AI-Starter-Kit-OnFHIR)
