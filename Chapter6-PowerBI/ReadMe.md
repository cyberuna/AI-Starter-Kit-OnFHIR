# Chapter 6 - Power BI: Analyze the FHIR bundles

This chapter shows 2 options to connect and analyze health records with PowerBI.

## Prerequisites
* [PowerBI Desktop](https://powerbi.microsoft.com/en-us/downloads/)
* Knowledge of [PowerBI](https://docs.microsoft.com/en-us/power-bi/guided-learning/)
* Knowledge of [PowerQuery](https://docs.microsoft.com/en-us/power-query/) & [M formula language](https://docs.microsoft.com/en-us/powerquery-m/)

Power BI is a business analytics service provided by Microsoft. Power BI lets you easily connect to your data sources, visualize and discover what’s important, and share with anyone you want.

## Connect to SQL DB
This option shows how 10 resource types of FHIR data - parsed using Azure Databricks and stored in SQL DB - can be analyzed in Power BI.

* Open PowerBI Desktop
* Connect to the SQL DB from PowerBI desktop and use this sample query. This query uses 10 resource types and you can update as needed.

```
SELECT * 
FROM Organization O 
JOIN Location L ON O.organizationid = L.organizationid
JOIN (
	SELECT 
		P.practitionerid
		,P.practitionercode
		,street
		,city
		,postalcode
		,state
		,country
		,gender
		,firstname
		,lastname
		,contact
		,PR.practitionerroleid
		,PR.locationid
		,PR.organizationid
		,PR.practitionername
	FROM Practitioner P
	JOIN PractitionerRole PR ON P.practitionerid = PR.practitionerid) P ON O.organizationid = P.organizationid AND L.locationid = P.locationid
LEFT OUTER JOIN Claim C ON L.locationid = C.locationid AND O.organizationid = C.organizationid 
LEFT OUTER JOIN Encounter E ON C.encounterid = E.encounterid 
LEFT OUTER JOIN Observation OB ON E.encounterid = OB.encounterid  
LEFT OUTER JOIN ExplanationOfBenefit EOB ON C.encounterid = EOB.encounterid AND C.claimid = EOB.claimid
LEFT OUTER JOIN Patient PT ON PT.patientid = EOB.patientid
```
* Analyze and visualize using Power BI


## Connect to Azure API for FHIR
This option shows how to connect and analyze FHIR data stored in Azure API for FHIR from Power BI desktop.

* Open Power BI Desktop
* Go to Menu --> Edit Queries --> Edit Queries --> Advanced Editor and paste the following:

```
let

 url = "https://login.microsoftonline.com/<tenantid>/oauth2/token",

 GetJson = Web.Contents(url,
     [
         Headers = [#"Content-Type"="application/x-www-form-urlencoded;charset=UTF-8"],
         Content = Text.ToBinary("grant_type=client_credentials&client_id=<clientid>&client_secret=<clientsecret>&resource=<audience>") 
     ]
 ),
 FormatAsJson = Json.Document(GetJson),

 AccessToken = FormatAsJson[access_token],
 AccessTokenHeader = "bearer " & AccessToken,

GetJsonQuery = Web.Contents("<audience>/Patient",
     [
         Headers = [#"Authorization"=AccessTokenHeader]
     ]
 ),
 FormatAsJsonQuery = Json.Document(GetJsonQuery),
 MyJSONTable = Table.FromRecords({FormatAsJsonQuery})
in
    MyJSONTable
```

* Use Power Query to parse the json and prepare the data
* Analyze and visualize using Power BI
 
***

[Go to Chapter 7 - Open Source FHIR Server: Create and Configure](../Chapter7-OpenSourceFHIRServer/ReadMe.md)

