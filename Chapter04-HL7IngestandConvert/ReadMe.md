# Chapter04 - HL7 Ingest and Convert

#### This chapter provides reference architecture and sample deployments for the ingest and conversion of HL7 messages and the de-identification of FHIR resources.

These samples demonstrate incorporating Microsoft's FHIR Converter into your enterprise HL7 messaging/FHIR infrastructure to enable end-to-end workflows for a variety of use cases. The examples include:
   * An HL7 ingest platform to consume HL7 Messages via MLLP and securely Transfer them to Azure via HL7overHTTPS and place in blob storage and produce a consumable event on a high speed ordered service bus for processing.
   * A workflow that performs orderly conversion from HL7 to FHIR via the conversion API and persists the message into a FHIR Server and publishes change events referencing FHIR resources to a high speed event hub to interested subscribers.

## Deploy using [Step by Step Instructions](https://github.com/microsoft/OpenHack-FHIR/tree/main/Challenge02-HL7IngestandConvert) to ingest HL7 messages and convert them into FHIR.

*** 

[Home](https://github.com/cyberuna/AI-Starter-Kit-OnFHIR)
