# ETL and Data Loads (Walmart data) -- Mini Project

ETL and Data Loads (Walmart data), Data Engineering Diploma Program, WeCloudData

Content developed by: WeCloudData Academy

## 1. Project Requirements

### Step 1 - Load The Original Dataset

You have a set of data. The dataset includes tables **store**, **product**, **inventory**, **sales** and **calendar**. These are the tables from operational databases.

![os_db_walmart](https://user-images.githubusercontent.com/108837052/201822898-b317b912-ab73-44b8-b401-030b476ec971.jpg)

You need to download the dataset from [this link](https://s3.amazonaws.com/weclouddata/data/walmart%20raw%20data.zip) and load the data into a schema of the Snowflake data warehouse. (It is easier to load the csv files from DBeaver)

![dbeaverimportdata](https://user-images.githubusercontent.com/108837052/201823064-f7225db3-bcad-49ab-b210-ca5cbb43e935.png)

You can use [this script](https://s3.amazonaws.com/weclouddata/data/data/build_os_db.sql) to build the schema for the original system dataset tables.

### Step 2 - Read and Understand the Business Requirements and data model

