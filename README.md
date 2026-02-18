# Microsoft-fabric-series-Project-4-Metadata-Driven-Incremental-Data-Pipeline
This project demonstrates the implementation of a folder-based incremental data ingestion pipeline using Azure Data Factory and Lakehouse architecture, followed by data cleaning, transformation, and aggregation using Spark.  The pipeline processes only new or modified files by tracking file metadata, ensuring efficiency and scalability.
-----------------------------------------------------------------------------------------------------------------------------------------------------
# Datasets Used
Orders
Customers
Products
Order Items
Each dataset arrives in a folder-based structure in ADLS Gen2.
-------------------------------------------------------------------------------------------------------------------------------------------------------
# Incremental Loading Strategy

Used Get Metadata to extract file names and lastModified timestamps

Used Lookup to fetch last_load_time from a file_tracker table

Applied conditional logic to process only updated files

Implemented parameterized pipelines to reuse logic across datasets

Updated file_tracker after successful ingestion
-----------------------------------------------------------------------------------------------------------------------------------------------------------
Medallion Architecture
# Bronze Layer
-----------------------------------------------------------------------
Raw data ingestion from ADLS Gen2 to Lakehouse

# Silver Layer (Data Cleaning & Validation)
--------------------------------------------------------------
Standardized date formats

Normalized categorical values (yes/y → yes)

Type casting (string, int, double)

Removed invalid records (e.g., quantity ≤ 0)

# Gold Layer (Business Aggregations)
------------------------------------------------------------------
Customer-level KPIs:

Order count

Total quantity & revenue

Average & max delivery delay

Delayed order count (> 3 days)

Total shipment cost

Discounted revenue

# Tech Stack
----------------------------------------------------------------

Azure Data Factory

Azure Data Lake Gen2

Lakehouse

Spark (PySpark)

SQL (File Tracker Table)
