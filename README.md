# big-data-challenge

In this challenge, two Amazon review datasets were extracted, transformed, and loaded. The two datasets used were:
1. https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Wireless_v1_00.tsv.gz
2. https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Watches_v1_00.tsv.gz

These datasets were loaded using PySpark and transformed using Pandas. To transform the data, the following methods were used:
1. .select to pull the data column values directly
2. col() and .cast to cast values from string type to integer or date type
3. .drop_duplicates to remove duplicate rows as required by the schema unique sql constraints on some product ids
4. .groupby and .agg to group rows by value and aggregate the column counts
5. .withColumnRenamed to rename aggregate column name to SQL column name

The review_id_df, products_df, customers_df, and vine_df dataframes were mapped to RDS in the review_id_table, products, customers, and vine_table tables respectively. For the first review dataset (wireless), the dataframes were mapped into the big-data database. For the second review dataset (watches), the dataframes were mapped into the big-data-2 database.