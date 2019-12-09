# Chapter 5 - Azure Databricks: Parse json and load into Azure SQL DB

Azure Databricks is a fast, easy, and collaborative Apache SparkTM–based analytics service. Spark SQL is a Spark module for structured data processing.

Create a SQL Server and SQL Database to load data for all specified resource types.

This Databricks [notebook]() shows:
* Mount the storage account containing the ndjson files from ADF
* Create and load each of the resource types into temporary tables
* Parse the json fields from each of these temporary tables
* Create a connection to a SQL DB 
* Create tables for each of these resource types
* Insert required parsed data from temporary tables into the tables in SQL DB

***

[Go to Chapter 6 - PowerBI: Analyze the FHIR bundles](./Chapter6/PowerBI.md)
