# AzureCosmosDB-To-Snowflake
## Problem
I have data in Azure CosmosDB with NoSQL API My CosmosDB is also Linked with Azure Synapse Analytics; I want to create Data Warehouse in Snwoflake on Top of CosmosDB; Snowflake shoudl run 1 time daily; No Duplicate records should upload in Snowflake; if Primary key is already exists in snowflake table then PIPE Line should update row in snowflake with updated outputs
## Solution

### 2. Alteryx

We need two ODBC Driver 1. Azure CosmosDB 2. Snowflake to connect both data 
if we use Alteryx we do not need to create Stage in Snowflake but we need ODBC Driver for both Database

1. Azure CosmosDB ODBC Driver https://learn.microsoft.com/en-us/azure/cosmos-db/odbc-driver
2. Snowflake ODBC Driver https://www.snowflake.com/en/developers/downloads/odbc/

After Downloading you need to configer both ODBC Driver then Open Alteryx;

The Challage is we do not have direct option to connect CosmosDB ODBC Connected so just click on file and goto Connection Management

+ Select Microsoft Analytics Platform System ODBC
Connection Name -- We can give it at own choise
Data Source Name -- We can give it at own choise
ODBC DNS -- your ODBC DNS Name;


Authentication Method Select  **No Credentials** because our Credentials is alraedy given in ODBC configuration;


Here is Example

<img
src="https://github.com/afzal94551/Data_PIPE_in_Different_Tech/blob/00d7a12ce0ebd5c0ddee850fe35c585c486b7d11/Create_Connection_Cosmos_1.png" width="800"/>








