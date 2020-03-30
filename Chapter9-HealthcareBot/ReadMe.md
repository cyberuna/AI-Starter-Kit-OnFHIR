# Chapter 9 - Appointment Scheduler Healthcare Bot

#### This chapter is sub-version of [HealthBot](https://docs.microsoft.com/en-us/HealthBot/) focusing on scheduling appointments. Click on the link for more details.

The Health Bot Service is a SaaS solution that empowers Microsoft partners to build and deploy compliant, AI-powered health agents, allowing them to offer their users intelligent, personalized access to health-related information and interactions through a natural conversation experience. 

This chapter focuses on how to use the "Booking appointments" template in HealthBot Service and allow users to schedule an appointment with a healthcare provider using FHIR easily and securely.

## Prerequisites
* [Azure API for FHIR R4 server](../Chapter2-AzureAPIforFHIR/ReadMe.md) with Patient, Schedule and Slot resources.
* Access to create SaaS [Microsoft Healthcare Bot Service](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/microsoft-hcb.microsofthealthcarebot).

## Steps
* Setup:\
Create a [Microsoft Healthcare Bot Service](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/microsoft-hcb.microsofthealthcarebot). Select a software plan and click Create.
* Configuration:\
You will receive an email from Azure Marketplace with a config link to the Health Bot Service admin portal. Once configuration is done, you will see the Health Bot Service home page.
* Authentication:\
Click Integration --> Authentication from the left navigation and click '+ New'.\
-- Enter Name for 'Authentication provider'. \
-- Choose "OAuth 2.0: Server-to-server authorization" in 'Authentication method'.\
-- Enter your Azure API for FHIR Client ID in 'Client ID'. You can find this in your Azure API for FHIR app registration.\
-- Enter your Azure API for FHIR Client Secret in 'Client Secret'. You can find this in your Azure API for FHIR app registration.\
-- Enter https://login.microsoftonline.com/tenantid/oauth2/v2.0/token in 'Access Token URL'. You can find this in Authority under Authentication in your Azure API for FHIR service.\
-- Check if your Object ID has been added to 'Allowed Object IDs' in your Azure API for FHIR service.\
-- Enter https://myfhir.azurehealthcareapis.com/.default in 'Scope'.\
-- Click 'Update'.
* Data Connection:\
Click Integration --> Data connections from the left navigation and click '+ New'.\
-- Enter Name for 'Data connection'.\
-- Turn on 'FHIR Support'.\
-- Enter https://myfhir.azurehealthcareapis.com for 'Base URL'. You can find this in Audience under Authentication in your Azure API for FHIR service.\
-- Choose the Authentication Provider create above in 'Authentication provider'.\
-- Click 'Update'.
* Template Catalog:\
-- Expand 'Scenarios' in the left navgation and click 'Template catalog'.\
-- Click 'Booking appointments' and click 'Import template'.\
-- The visual designer will open with the template. The imported template will appear under 'Scenarios' --> 'Manage'. Clicking on the name of the template will also open the template in visual designer.
* Design and Coding: Updated Template\
** Schedule and Slot has to be available for the service types on your Azure API for FHIR.\
** This template was enhanced to work to create an appointment.\
-- Click the 'Code' tab on the bottom left.\
-- Copy and paste from the [Updated Template](./UpdatedFHIRTemplate.json).\
-- Edit names of 'authenticationProvider' and 'dataConnection' in the file to the ones you created in steps above.\
-- Save and Exit.\
-- Open the file and click 'Run' at the top.
* Design and Coding: From Template Catalog\
** Schedule and Slot has to be available for the service types on your Azure API for FHIR.\
** This template has building blocks but needs design and coding changes before ready to create an appointment.\
** The following changes needs to done for every Data Connection in the template.\
-- Double-click or right-click --> Edit on every Data Connection that is in oval shape.\
-- Copy the 'Payload' and save somewhere as you will need it.\
-- Choose the Data Connection created above.\
-- Check if the right Base URL appears in 'Base URL'.\
-- Change 'Path' to not have / or quotes as pre-fix or post-fix. Example: Patient and not /Patient or 'Patient'\
-- 'Payload' will be grayed out for 'Read'. Copy the copied and saved Payload into the 'Payload' box for 'Create'. Changing the Data Connection causes the fields in Payload to disappear.\
-- Save and Exit.\
-- Re-open and test by right-clicking on any and click 'Run from here'.
* Web Chat:\
Check this to [Embed Health Bot service in Web](https://github.com/Microsoft/HealthBotcontainersample)



*** 


