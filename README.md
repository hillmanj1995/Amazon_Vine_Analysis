# Amazon Vine Analysis

## Overview & Purpose
The Analyst was tasked with the analyzing Amazon reviews written by members of the paid Amazon Vine program. The Amazon Vine program is a service that allows manufacturers and publishers to receive reviews for their products. Companies like SellBy (who The Analyst just completed a project for) pay a small fee to Amazon and provide products to Amazon Vine members, who are then required to publish a review.

The Analyst picked a dataset of outdoor products from an AWS database then used PySpark to perform the ETL process to extract and transform the data, then connected to an AWS RDS instance and loaded the transformed data into pgAdmin.  After the ETL process, The Analyst used PySpark to determine if there is any bias toward favorable reviews from Vine members in the dataset.

## Results
The dataset had over 2 million reviews entered, so in an effort to identify the most helpful data, The Analyst filtered the dataset into dataframes containing total votes greater than or equal to 20, and from there, further filtered the dataframe to show the reviews where the number of helpful votes were greater than or equal to 50%. Both data frames can be seen below:

    Total Votes Greater Than or Equal to 20:
    ![filtered_vine.png](https://github.com/hillmanj1995/Amazon_Vine_Analysis/blob/main/Resources/filtered_vine.png)

    Reviews Where Helpful Votes Were Greater Than or Equal to   50%:
    ![helpful_vine.png](https://github.com/hillmanj1995/Amazon_Vine_Analysis/blob/main/Resources/helpful_vine.png)

With that helpful_vine dataframe, The Analyst was able to then filter the data between Vine reviewed (paid) and non-Vine reviewed (unpaid) items.  Those dataframes are shown below:

    Vine Reviewed Items:
    ![paid_df.png](https://github.com/hillmanj1995/Amazon_Vine_Analysis/blob/main/Resources/paid_df.png)

    Non-Vine Reviewed Items:
    ![unpaid_df.png](https://github.com/hillmanj1995/Amazon_Vine_Analysis/blob/main/Resources/unpaid_df.png)

Using those dataframes, the following questions were able to be answered:

1. How many Vine reviews and non-Vine reviews were there?

    The Analyst used the following code to get a count of the total number of Vine (paid) and non-Vine (unpaid) reviews in the filtered dataset.

    ![total_paid_reviews.png](https://github.com/hillmanj1995/Amazon_Vine_Analysis/blob/main/Resources/total_paid_reviews.png)

    ![total_unpaid_reviews.png](https://github.com/hillmanj1995/Amazon_Vine_Analysis/blob/main/Resources/total_unpaid_reviews.png)

    The resulting counts show that there were far more non-Vine (unpaid) reviews (39,869 reviews) than there were Vine (paid) reviews (107 reviews).

2. How many Vine reviews were 5-stars? How many non-Vine reviews were 5-stars?

    The Analyst filtered the Vine (paid) and non-Vine (unpaid) datasets to provide counts of the number of 5-star reviews for each.  The code for those counts are shown below:

    ![total_paid_5_star_reviews.png](https://github.com/hillmanj1995/Amazon_Vine_Analysis/blob/main/Resources/total_5_star_paid_reviews.png)

    ![total_unpaid_5_star_reviews.png](https://github.com/hillmanj1995/Amazon_Vine_Analysis/blob/main/Resources/total_5_star_unpaid_reviews.png)

    Like the result from the total amount count of reviews, there were far more non-Vine (unpaid) 5-star reviews (21,005 reviews) than there were Vine (paid) reviews (56 reviews).

3. What percentage of Vine reviews were 5 stars? What percentage of non-Vine reviews were 5 stars?

    Using the results from the above questions, The Analyst was able to calculate the percentage of 5-star Vine (paid) and non-Vine (unpaid) reviews against their respective total counts.  The code for those calculations are shown below:

    ![percent_paid_5_star_reviews.png](https://github.com/hillmanj1995/Amazon_Vine_Analysis/blob/main/Resources/percent_5_star_paid_reviews.png)

    ![percent_unpaid_5_star_reviews.png](https://github.com/hillmanj1995/Amazon_Vine_Analysis/blob/main/Resources/percent_5_star_unpaid_reviews.png)

The result for these calculations showed that the percentages of 5-star reviews for both Vine (pain) and non-Vine (unpaid) against their totals were very similar: 52.34% for Vine (paid) reviews, and 52.68% for non-Vine (unpaid) reviews.

## Summary
Based on the results above, there does not seem to be any positivity bias between the Vine (paid) vs. non-Vine (unpaid) reviews as the percentage of 5-star reviews against the total paid and unpaid review count was roughly the same (52.34% for Vine (paid) reviews vs. 52.68% for non-Vine (unpaid) reviews). 

To further investigate whether there is a bias among Vine reviewers would be to do the same analysis for different products to see if the review results change by product type.
