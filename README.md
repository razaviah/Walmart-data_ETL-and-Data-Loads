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

We have create the data model. You need to populate the data from the original schema to the data model schema. 

First of all, The data model has 3 dimensions : **store**, **date**, **product**.

For the fact table, we need 2 fact tables:

* Daily fact table: On the daily level, the row grain is date + store + product. In the daily fact table, in addition to the existing columns from the sales and inventory tables, in the fact table we need one more column called "low_stock_flg". This flag is True when sales_qty in the sales table lower than the stock_on_hand_qty in the inventory at that date.

* Weekly fact table: We need the second fact table on weekly base. This week table contains all the aggregate values from the daily fact table and also includes some new columns:
  * eop_stock_on_hand_qty: This is the on hand stock qty at the end of week (Saturday), which means the on hand stock qty of the last day in the week. So you can't simply aggregate it.
    * eop_stock_on_order_qty: This is the on order stock qty at the end of week (Saturday).
    * out_of_stock_times: During one week, how many times when the out_of_stock_flg is True.
    * in_of_stock_times: During one week, how many times when the in_of_stock_flg is True.
    * low_stock_times: During one week, how many times when the low_stock_flg is True. 
