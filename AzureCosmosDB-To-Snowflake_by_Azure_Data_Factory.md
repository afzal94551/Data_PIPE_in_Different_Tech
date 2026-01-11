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


 ### Step 1 Add Source flow 

Source Step 1 - You need to create a Data Set for both Source and Destination then blow 6 Steps; you source is created. 

<img
src="https://github.com/afzal94551/Data_PIPE_in_Different_Tech/blob/f9e28302d1d949765b64970a274e2fcc7687de0a/Cosmos_Input_Part1.png" width="800"/>


Source Step 2

<img
src="https://github.com/afzal94551/Data_PIPE_in_Different_Tech/blob/f9e28302d1d949765b64970a274e2fcc7687de0a/Cosmos_Input_Part2.png" width="800"/>

Source Step 3

<img
src="https://github.com/afzal94551/Data_PIPE_in_Different_Tech/blob/f9e28302d1d949765b64970a274e2fcc7687de0a/Cosmos_Input_Part3.png" width="800"/>

Source Step 4

<img
src="https://github.com/afzal94551/Data_PIPE_in_Different_Tech/blob/f9e28302d1d949765b64970a274e2fcc7687de0a/Cosmos_Input_Part4.png" width="800"/>

Source Step 5

<img
src="https://github.com/afzal94551/Data_PIPE_in_Different_Tech/blob/f9e28302d1d949765b64970a274e2fcc7687de0a/Cosmos_Input_Part5.png" width="800"/>

Source Step 6

<img
src="https://github.com/afzal94551/Data_PIPE_in_Different_Tech/blob/29d48a8635a0276fd410568f339e6e38ad669df8/Cosmos_Input_Part6.png" width="800"/>
 

+ ** Your  Data Source is Connected Successfully **

** Now create Source for Snowflake table whare you want to insert/update data from Azure CosmosDB; **


### Step 2  Add New Flow ** JOIN **
Cretae Join Left Join Left Table should your Sourse table and right should your destination to check if record already found in source;

here is the example.

<img 
src="https://github.com/afzal94551/Data_PIPE_in_Different_Tech/blob/d36f5bf4f781272a03933900a905d43b29032c92/Join%20Step%201.png" 
width="800"/>

### Step 3 Add New Flow ** FilterRow **
Add FilterRow and give condition
For example I want to update snowflake table if my Product_Id already exists in Snowflake table else insert as new item;
I have may option if can delete data from Snowflake;


Here is example ; 

<img
src="https://github.com/afzal94551/Data_PIPE_in_Different_Tech/blob/7ca27d91caa066cf29e9e393b4e745e7a7b04fb8/Filter%20Step%201.png"
width="800"/>


### Final Step - Add Flow ** Sink **
here is some example with step by step

Step 1- Sink

<img
src="https://github.com/afzal94551/Data_PIPE_in_Different_Tech/blob/7ca27d91caa066cf29e9e393b4e745e7a7b04fb8/Destination%20Step%201.png"
width="800"/>

Step 2  Setting
in Update method i have selected only **Allow Insert and Allow Update** but you can you as per your requirement;


Select Key Column - your Unique Identifier for me it is Product_id;

also you can you Table Action- if you want truncate or recreate table;
<img
src="https://github.com/afzal94551/Data_PIPE_in_Different_Tech/blob/7ca27d91caa066cf29e9e393b4e745e7a7b04fb8/Destination%20Step%202.png"
width="800"/>

Step 3 Error
in Link Service you need to link your Blob Storage 
<img
src="https://github.com/afzal94551/Data_PIPE_in_Different_Tech/blob/7ca27d91caa066cf29e9e393b4e745e7a7b04fb8/Destination%20Step%203.png"
width="800"/>

Step 4 Mapping 
Now you need to map column name of both Database;
<img
src="https://github.com/afzal94551/Data_PIPE_in_Different_Tech/blob/7ca27d91caa066cf29e9e393b4e745e7a7b04fb8/Destination%20Step%204.png"
width="800"/>

then you should preview and Test you flow


+ ** Now your Data Flow is ready to you you need to create a Pipeline
 Add your Dataflow in Pipline then your can Schedule your Pipline as per your requirement'













