# AzureCosmosDB-To-Snowflake
## Problem 
I have data in Azure CosmosDB with NoSQL API My CosmosDB is also Linked with Azure Synapse Analytics;
I want to create Data Warehouse in Snwoflake on Top of CosmosDB; 
Snowflake shoudl run 1 time daily;
No Duplicate records should upload in Snowflake; if Primary key is already exists in snowflake table then PIPE Line should update row in snowflake with updated outputs


## Solution
### 1. Azure Data Factory

Lets Create a Dataflow to Get Data from Azure CosmosDB and insert and update Snowflake table
