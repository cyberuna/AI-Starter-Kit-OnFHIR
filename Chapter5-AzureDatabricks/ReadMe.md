# Chapter 5 - Azure Databricks: Parse json and load into Azure SQL DB

This chapter shows how to setup Azure Databricks, parse and load health records into Azure SQL DB.

## Prerequisites
* Knowledge of [Azure Databricks](https://docs.microsoft.com/en-us/azure/azure-databricks/what-is-azure-databricks)
* Knowledge of [Azure SQL Database](https://docs.microsoft.com/en-us/azure/sql-database/)
* Knowledge of [Spark SQL](https://docs.microsoft.com/en-us/azure/databricks/spark/latest/spark-sql/)

Azure Databricks is a fast, easy, and collaborative Apache SparkTM–based analytics service. Spark SQL is a Spark module for structured data processing.

Create a SQL Server and SQL Database to load data for all specified resource types.

This Databricks [notebook](./fhirdatabrickstemplate.ipynb) includes:
* Connect to the storage account containing the ndjson files from Azure Data Factory.

```
storageAccountName = <mystorageaccount>
storageAccountKey = <mystoragekey>

if not any(mount.mountPoint == '/mnt/dataexport' for mount in dbutils.fs.mounts()):
  dbutils.fs.mount(
    source = "wasbs://dataexport@" + storageAccountName + ".blob.core.windows.net",
    mount_point = '/mnt/dataexport',
    extra_configs = {"fs.azure.account.key." + storageAccountName + ".blob.core.windows.net":storageAccountKey})
```

* Create and load each of the resource types into temporary tables
```
%sql 
DROP TABLE IF EXISTS patientTable;
CREATE TEMPORARY TABLE patientTable USING json OPTIONS (path "/mnt/dataexport/Patient.json");
```

* Create tables for each of these resource types based on the json file. Create the Patient table in SQL Database using SQL Management Studio or Azure Portal.
```
%sql
DROP TABLE IF EXISTS jdbcPatientTable;
CREATE TABLE jdbcPatientTable
USING org.apache.spark.sql.jdbc
OPTIONS (
  url "jdbc:sqlserver://<mysqlserver>.database.windows.net:1433;database=<mysqldatabase>",
  dbtable "dbo.Patient",
  user <myuser>,
  password <mypassword>
);
```
* Insert required parsed data columns from temporary tables into the tables in SQL DB
```
%sql
INSERT INTO jdbcPatientTable
SELECT id as patientid, name.family[0] as lastname, name.given[0] as firstname, maritalStatus.coding[0].display as maritalStatus, birthDate, gender, address.line[0] as streetname, address.city[0] as city, address.postalCode as postalCode, address.state[0] as state, address.country[0] as country, telecom.value as phone, address[0].extension[0].extension.valueDecimal[0] as latitude, address[0].extension[0].extension.valueDecimal[0] as longitude from patientTable;
```

* Add this notebook to Azure Data Factory
Create a linked service in the Data Factory to point to this notebook. 
Create a pipeline to run this notebook.

***

[Go to Chapter 6 - PowerBI: Analyze the FHIR bundles](../Chapter6-PowerBI/ReadMe.md)
