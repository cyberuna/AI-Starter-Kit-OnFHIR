# Chapter 1 - Synthea: Generate FHIR patient and financial bundles

#### This chapter shows how to setup and generate health records with Synthea.

Synthea is an open-source synthetic patient and associated health records generator that simulates the medical history of synthetic patients.
Synthea generates HL7 FHIR records using the HAPI FHIR library to generate a FHIR Bundle for [these](https://github.com/synthetichealth/synthea/wiki/HL7-FHIR) FHIR Resources.
More on Synthea [here](https://github.com/synthetichealth/synthea).

By default, Synthea contains publicly available demographic data obtained from the US Census Bureau. The data was post-processed to create population input data for every place (town and city) in the United States. This post-processed data can be used with Synthea to generate representative populations. (County + SubCounty + Education + Income).  See https://github.com/synthetichealth/synthea/wiki/Default-Demographic-Data for details.

## Prerequisites
* Java 1.8 (select JDK, not JRE install)

## Setup Synthea
* Follow the [setup](https://github.com/synthetichealth/synthea/wiki/Basic-Setup-and-Running) instructions and download the .jar file.
* Copy [synthea.properties](./synthea.properties) file to the same location as the .jar file downloaded above.
* Run the 'run_synthea' batch file with the parameters. run_synthea [-h][-s seed] 
            [-cs clinician seed]
            [-p populationSize]
            [-g gender]
            [-a minAge-maxAge]
            [-m moduleFilter]
            [-c localConfigFilePath]
            [-d localModulesDirPath]
            [state [city]]. More examples in the link above.
* (Optionally) configure the United States source demographics *.csv data with entries helpful to your subject demographics:
    * [Provider](https://github.com/synthetichealth/synthea/wiki/Provider-Data)
    * [Payer](https://github.com/synthetichealth/synthea/wiki/Payer-Data)
    * [Cost Data - Encounter, Procedure, Medication, Immunization, Regional Adjustment Factors](https://github.com/synthetichealth/synthea/wiki/Cost-Data)
    * [Person Name](https://github.com/synthetichealth/synthea/wiki/Name-Data)
    * [Zip/Postal code](https://github.com/synthetichealth/synthea/wiki/Zip-or-Postal-Codes) 
* Output json files will be saved in output folder in the same directory.

Detailed Example:\
To generate data for 100 patients using a seed (unique root of data generation) of 777 in Texas using the associated synthea properties settings:\
-- Copy [run_synthea](./run_synthea.bat) file to the same location as the .jar file downloaded above.\
-- Edit the file with your folder locations.\
-- Run the bat file to generate json files to the output folder in the same directory.

COVID-19 Data Example:\
-- To generate 50 COVID patients, run this: java -jar synthea-with-dependencies.jar -m "covid19" -p 50


***

[Go to Chapter 2 - Azure API for FHIR: Create and configure](../Chapter2-AzureAPIforFHIR/ReadMe.md)
