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

for Credentials
<img
src="https://github.com/afzal94551/Data_PIPE_in_Different_Tech/blob/00d7a12ce0ebd5c0ddee850fe35c585c486b7d11/Create_Connection_Cosmos_2.png" width="800"/>

Now Create Connecto for Snowflake

Data Source Connection
<img
src="https://github.com/afzal94551/Data_PIPE_in_Different_Tech/blob/00d7a12ce0ebd5c0ddee850fe35c585c486b7d11/Create_Connection_Snowflake_1.png" width="800"/>

Credentials Configuration
<img
src="https://github.com/afzal94551/Data_PIPE_in_Different_Tech/blob/00d7a12ce0ebd5c0ddee850fe35c585c486b7d11/Create_Connection_Snowflake_2.png" width="800"/>

Now Create Input Data Flow and connect with your Azure CosmosDB Connetion that;

here is flow example;

<img
src="https://github.com/afzal94551/Data_PIPE_in_Different_Tech/blob/00d7a12ce0ebd5c0ddee850fe35c585c486b7d11/Alteryx_Flow_1.png"
width="800"/>

use Select tool to select require column and match column names 
<img
src="https://github.com/afzal94551/Data_PIPE_in_Different_Tech/blob/00d7a12ce0ebd5c0ddee850fe35c585c486b7d11/Alteryx_Flow_2.png"
width="800"/>


Now Add a Output Data Flow and Configure 
1. Table give your Snowflake Table name where you want to insert to update data
2. Output Options - choose your option in my case  I have choose ** Update: Insert if New ** this flow will check if record found then it will udpate else it will create new records
3. Append Field Map - this is for Mapping  I choose By Field Name
4. Key for Update - Select your Priamary Key or Unique Indetifier

here is example

<img
src="https://github.com/afzal94551/Data_PIPE_in_Different_Tech/blob/00d7a12ce0ebd5c0ddee850fe35c585c486b7d11/Alteryx_Flow_3.png"
width="800"/>


+ **Your Pipeline is create;**















