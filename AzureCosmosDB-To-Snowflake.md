# AzureCosmosDB-To-Snowflake
## Problem 
I have data in Azure CosmosDB with NoSQL API My CosmosDB is also Linked with Azure Synapse Analytics;
I want to create Data Warehouse in Snwoflake on Top of CosmosDB; 
Snowflake shoudl run 1 time daily;
No Duplicate records should upload in Snowflake; if Primary key is already exists in snowflake table then PIPE Line should update row in snowflake with updated outputs


## Solution
### 1. Azure Data Factory

Lets Create a Dataflow to Get Data from Azure CosmosDB and insert and update Snowflake table

Azure Data Factory Data Flow Image;

<img src="https://github.com/afzal94551/Data_PIPE_in_Different_Tech/blob/bd172261eaaabf2614585271edc66c544ff1754c/FromAzureCosmosToSnowflake_DataFlow.png" width="800"/>


Let go step by Step;

Add Source flow and flow below settings

Step 1

<img
src="https://github.com/afzal94551/Data_PIPE_in_Different_Tech/blob/f9e28302d1d949765b64970a274e2fcc7687de0a/Cosmos_Input_Part1.png" width="800"/>


Step 2

<img
src="https://github.com/afzal94551/Data_PIPE_in_Different_Tech/blob/f9e28302d1d949765b64970a274e2fcc7687de0a/Cosmos_Input_Part2.png" width="800"/>

Step 3

<img
src="https://github.com/afzal94551/Data_PIPE_in_Different_Tech/blob/f9e28302d1d949765b64970a274e2fcc7687de0a/Cosmos_Input_Part3.png" width="800"/>

Step 4

<img
src="https://github.com/afzal94551/Data_PIPE_in_Different_Tech/blob/f9e28302d1d949765b64970a274e2fcc7687de0a/Cosmos_Input_Part4.png" width="800"/>

Step 5

<img
src="https://github.com/afzal94551/Data_PIPE_in_Different_Tech/blob/f9e28302d1d949765b64970a274e2fcc7687de0a/Cosmos_Input_Part5.png" width="800"/>

Step 6

<img
src="https://github.com/afzal94551/Data_PIPE_in_Different_Tech/blob/29d48a8635a0276fd410568f339e6e38ad669df8/Cosmos_Input_Part6.png" width="800"/>




