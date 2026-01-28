## DATASET

[Classified Ads for Cars](https://www.kaggle.com/datasets/mirosval/personal-cars-classifieds)


Note: Instead of downloading from Kaggle, download it from [this URL](https://bit.ly/ClassifiedCars). 
The data was scraped from several websites in the Czech Republic and Germany over a period of more than a year.

> You can directly download the dataset to your local using the following command:
> 
> `wget https://bit.ly/ClassifiedCars -O cars.zip`
> 
> After downloading, you can extract the dataset using the following command:
> 
> `unzip cars.zip && rm cars.zip`

## TASKS

After transferring data to HDFS, use Apache Hive Query Language (HQL):

1. Write a Hive query to create a table called used_cars from the data. 
2. Write several Hive queries to find how many missing values (NULL in an attribute of a record) you have in each column (attribute).
3. Drop the columns (attribute) with more than 50% missing values. (For example if 50% or more of `body_type` is missing, drop `body_type` column using `REPLACE COLUMNS` using HQL)
4. Write several Hive queries to create a new table called `clean_used_cars` from `used_cars` with the following conditions:

  * The manufacturing year between 2000 and 2017 including 2000 and 2017
  * Both maker and model exist (NOT NULL) in the row
  * The price range is from 3000 to 2,000,000 (3000 ≤ price ≤ 2,000,000)

5. Write Hive to find how many records remained clean_used_cars.
6. Write a Hive query to find the make and model for the cars with the top 10 highest average prices.
7. Write a Hive query to find the make and model for the cars with the top 10 lowest average prices.
8. Write a Hive query to recommend the top five make and models for **Economic Segment** customers
  * **Economic Segment**: Top five manufacturers in the 3000 to 20,000 price range; `3000 ≤ price < 20,000` based on the top average price.
9. Write a Hive query to recommend the top five make and models for **Intermediate Segment** customers
  *  **Intermediate Segment**: Top five manufacturers in the 20,000 to 300,000 price range; `20,000 ≤ price < 300,000` based on the top average price.
10. Write a Hive query to recommend the top five make and models for the **Luxury Segment** customers
  *  **Luxury Segment**: Top five manufacturers in the 300,000 to 2,000,000 price range; `300,000 ≤ price < 2,000,000` based on the top average price.

## HINT

Assume the following table is the `clean_used_cars` table:
<pre>
BMW X3           1000
BMW X5           10000
Honda Civic      500
Honda Fit        200
Honda Civic      300
Toyota Corolla   600
Tesla X          20000
Tesla X          15000
Tesla 3          10000
Tesla Y          12000
BMW X3           2000
</pre>

This is aggregation based on the average of make and model:
<pre>
BMW X3          1500
BMW X5          10000
Honda Civic     400
Honda Fit       200
Toyota Corolla  600
Tesla X         17500
Tesla 3         10000
</pre>

These are three segments: [0-2000], (2000,15000], (15000,20000]
<pre>
0 - 2000
Honda Fit
Honda Civic
Toyota Corolla
BMW X3

2000-15000
Tesla 3 
BMW X5

15000-20000
Tesla X
</pre>
