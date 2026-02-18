# Basic

#### Download Workshop Folder from AWS Jupyter 
Jupyter cannot download folders directly. Zip the folder and download the zip. 

Step 1: **Create zip of the full workshop 
**
import shutil
shutil.make_archive(
    "amazon-bedrock-agentcore-workshop",
    "zip",
    "/home/sagemaker-user/amazon-bedrock-agentcore-workshop"
)

step 2:  **Download to your PC ** 

from IPython.display import FileLink
FileLink('amazon-bedrock-agentcore-workshop.zip')

Click the link to download the zip file to your local machine. 


### Analytical DB (Analytical Database)
An analytical DB is a database designed to analyze large volumes of historical data to find patterns, trends, and insights. It is optimized for read-heavy, complex queries (aggregations, time-series analysis), not for frequent small updates.  

Examples of analytical databases:

1. Snowflake
2. Google BigQuery
3. Amazon Redshift

- Unpivot a DataFrame means converting columns into rows so the data becomes more long/normalized instead of wide. 
- Unpivot = columns → rows, useful for analytics, charts, and machine learning. 

#### Short Example - Before (wide format):  

| Machine | Temp | Vibration |
| ------- | ---- | --------- |
| M1      | 70   | 0.3       |
| M2      | 75   | 0.5       |


#### After Unpivot (long format): 

| Machine | Metric    | Value |
| ------- | --------- | ----- |
| M1      | Temp      | 70    |
| M1      | Vibration | 0.3   |
| M2      | Temp      | 75    |
| M2      | Vibration | 0.5   |
 
 
### Steps to convert the CSV file to Parquet format 

- CSV is simple and human-readable.
- Parquet is compact, faster, and better for large-scale analytics. 


**Step 1**: Setup and confirm the kernel environment  
```python
import sys
print("python:", sys.executable)

try:
    import pyarrow
    print("pyarrow:", pyarrow.__version__)
except Exception as e:
    print("pyarrow import failed:", repr(e))
```

**Step 2**:  Install pyarrow into this kernel 

```python
import sys
!{sys.executable} -m pip install --upgrade pyarrow
```
 

**Step 3**: Save as parquet  

```
data.to_parquet("data_timeseries.parquet", index=False, compression="snappy")
```
