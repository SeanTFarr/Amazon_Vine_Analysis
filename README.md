
<img src=Images\Vine_analysis.png>

## Overview of the analysis: 
Amazon Vine uses trusted reviewers to post opinions about new products to help inform other customers make informed decisions on their purchase. The purpose of this analysis was to select a data set of reviews from Amazon Review datasets to perform the ETL(Extract, Transform, Load) process on. Using Pyspark, I extracted the dataset, transformed the data by filtering the reviews, and then loaded the data into PGAdmin by conncting to an AWS RDS instance. Once loaded, Pyspark was used to further filter the dataset by separating out paid reviews(Vine) vs unpaid reviews(Non-Vine) to determine if having a paid Vine review makes a difference in the percentage of 5 star reviews.

### Resources used:
- Code: Pyspark, Python, SQL
- Code Editor: Google Colab
- Database: AWS RDS connected to PGAdmen
- Dataset: https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Home_Improvement_v1_00.tsv.gz

## Results: 
Following the ETL process,  we **extract**ed the dataset an created a new DataFrame

<img src=Images\df.jpg>

For the **transform**ing portion I had to separate the dataset into 4 distinct DataFrames that were **load**ed the 4 DataFrames into PGAdmin tables: 

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




Using the vine_df, I wanted to answer the following sets of questions:

- Vine Reviews
    - How many Vine reviews were there? 
    - How many Vine reviews were 5 stars? 
    - What percentage of Vine reviews were 5 stars? 
- Non-Vine Reviews
    - How many non-Vine reviews were there? 
    - How many non-Vine reviews were 5 stars? 
    - What percentage of non-Vine reviews were 5 stars?

To answer these, further filtering of the datasets was needed. 

First the DataFrame was filtered to show only the reviews with more than 20 total votes to pick reviews that are more likely to be helpful and to avoid having division by zero errors.

<img src=Images\filtered_df.jpg>

The DataFrame was then filtered to retreive all the rows where the number of helpful_votes divided by total_votes is equal to or greater than 50%.

<img src=Images\rows_df.jpg>

Finally, the new DataFrame was used to separate out the Vine and Non-Vine reviews into two DataFrames:

The Vine DataFrame

<img src=Images\vine_y.jpg>

The Non-Vine DataFrame:

<img src=Images\vine_n.jpg>

With these set up, I was able to determine the answers to the quesitons:

For Vine reviews

<img src=Images\vine_y_results.jpg>

For Non-Vine reviews

<img src=Images\vine_n_results.jpg>

## Summary: 

With the results of both the Vine and Non-Vine reviews having a similar percentage of 5 star reviews relative to their total reviews, it appears that there was no positivity bias occuring. In short, it looks like having a paid Vine review does not make a difference in the percentage of 5 star reviews.

An additional analysis of the dataset could further support this by looking at the 4 star ratings reviews to see if the results between the Vine and Non-Vine percentages are also similar.