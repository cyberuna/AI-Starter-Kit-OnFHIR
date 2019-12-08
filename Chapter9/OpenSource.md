# Chapter 9 - Open Source FHIR Server: Create and Configure

Synthea is an open-source synthetic patient and associated health records generator that simulates the medical history of synthetic patients.
Synthea generates HL7 FHIR records using the HAPI FHIR library to generate a FHIR Bundle for [these](https://github.com/synthetichealth/synthea/wiki/HL7-FHIR) FHIR Resources.
More on synthea [here](https://github.com/synthetichealth/synthea).

# Setup Synthea
Follow the [setup] (https://github.com/synthetichealth/synthea/wiki/Basic-Setup-and-Running) instructions.
Copy [synthea.properties](./synthea.properties) file to the same location as the .jar file downloaded from the previous step.
Run the jar file with the parameters. Example: java -jar synthea-with-dependencies.jar -s 1048576 -p 100 Texas -c <path>\synthea.properties 
Output json files will be saved in output folder in the same directory.


