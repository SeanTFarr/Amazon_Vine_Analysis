
<img src=Images\Vine_analysis.png>

## Overview of the analysis: 
The purpose of this analysis was to select a data set of reviews from Amazon Review datasets to perform the ETL(Extract, Transform, Load) process on. Using Pyspark we extracted the dataset, transformed the data by filtering the reviews, and then loaded the data into PGAdmin by conncting to an AWS RDS instance. Once loaded, we used Pyspark to further filter the dataset by separating out paid reviews vs unpaid reviews to determine if having a paid Vine review makes a difference in the percentage of 5 star reviews.

### Resources used:
- Code: Pyspark, Python, SQL
- Code Editor: Google Colab
- Database: AWS RDS connected to PGAdmen
- Dataset: https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Home_Improvement_v1_00.tsv.gz

## Results: 
Following the ETL process,  we extracted the dataset an created a new DataFrame

<img src=Images\df.jpg>

For the transforming portion we had to separate the dataset into 4 distinct DataFrames that were loaded the 4 DataFrames into PGAdmin tables: 

1. The customers_df loaded into customers_table 

<img src=Images\customers_df.jpg>
<img src=Images\SQLcustomers_table.jpg>

2. The products_df loaded into products_table 

<img src=Images\products_df.jpg>
<img src=Images\SQLproducts_table.jpg>

3. The review_id_df loaded into review_id_table 

<img src=Images\review_id_df.jpg>
<img src=Images\SQLreview_id_table.jpg>

4. The vine_df loaded into vine_table 

<img src=Images\vine_df.jpg>
<img src=Images\SQLvines_table.jpg>



<img src=>
Using bulleted lists and images of DataFrames as support, address the following questions:

- How many Vine reviews and non-Vine reviews were there?
- How many Vine reviews were 5 stars? 
- How many non-Vine reviews were 5 stars?
- What percentage of Vine reviews were 5 stars? 
- What percentage of non-Vine reviews were 5 stars?

## Summary: 
In your summary, state if there is any positivity bias for reviews in the Vine program. Use the results of your analysis to support your statement. Then, provide one additional analysis that you could do with the dataset to support your statement.