# Hive Lab: Analyzing Sales Data with Hive on Google Dataproc

## Objective: 
- To understand the basic concepts of Apache Hive, including creating tables, loading data and perform different aggregation operations on a sales data set using Google Dataproc cluster.

## Prerequisites: 
- A Google Cloud Platform account with access to Dataproc.
- Familiarity with the command line interface

## Step 1: Create a Dataproc Cluster
- Log in to your Google Cloud Platform account and navigate to the Dataproc dashboard.
- Click on the "Create cluster" button to create a new cluster with the default settings.
- SSH into the cluster's master node

## Step 2: Download sales data
- Use the command `wget https://raw.githubusercontent.com/tofighi/BigData/main/datasets/sales/sales_data.csv -P /var/tmp` to download the sales_data.csv file from the GitHub repository and save it in the /var/tmp directory
- Verify that the file has been downloaded by running the command `ls /var/tmp`

## Step 3: Move the file to HDFS
- Move the downloaded file to HDFS by using the command `hadoop fs -put /var/tmp/sales_data.csv /`
- Verify that the file has been moved to HDFS by running the command `hadoop fs -ls /`

## Step 4: Create a Hive database and table
- Open the Hive shell by running the command `hive` in the terminal.
- Create a new database named "sales_db" by running the command `CREATE DATABASE sales_db;`
- Use the database by running the command `USE sales_db;`
- Create a new table named "sales_data" using the command `CREATE TABLE sales_data (order_id INT, city STRING, province STRING, product_name STRING, product_price FLOAT, quantity INT) ROW FORMAT DELIMITED FIELDS TERMINATED BY ',';`
- Load the data from the "sales_data.csv" file into the table by running the command `LOAD DATA INPATH '/sales_data.csv' INTO TABLE sales_data;`

## Step 5: Perform Hive Queries and Aggregations
- Perform different queries as per your understanding and focus on the different aggregation concepts of Hive

## Step 6: Cleanup
- Drop the table by running the command `DROP TABLE sales_data;`
- Drop the database by running the command `DROP DATABASE sales_db;`
- Once you have finished the lab, you may delete the cluster to avoid incurring additional charges.

Note: You can also use the gsutil command to move the csv file from local to google cloud storage and then use the GCS path for the load statement.
