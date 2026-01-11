# AzureCosmosDB-To-Snowflake
## Problem
I have data in Azure CosmosDB with NoSQL API My CosmosDB is also Linked with Azure Synapse Analytics; I want to create Data Warehouse in Snwoflake on Top of CosmosDB; Snowflake shoudl run 1 time daily; No Duplicate records should upload in Snowflake; if Primary key is already exists in snowflake table then PIPE Line should update row in snowflake with updated outputs
## Solution

### 2. Alteryx

We need two ODBC Driver 1. Azure CosmosDB 2. Snowflake to connect both data 
if we use Alteryx we do not need to create Stage in Snowflake but we need ODBC Driver for both Database

1.   ![Azure CosmosDB ODBC Driver]("https://learn.microsoft.com/en-us/azure/cosmos-db/odbc-driver")
