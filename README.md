# Amazon Vine: Analysis
## Overview
The Amazon Vine program is a service that allows manufacturers and publishers to recieve reviews for their products. Companies pay a small fee to Amazon and provide products to Amazon Vine members, who then are required to publish a review. We will be analyzing Amazon reviews written by members of the paid Amazon vine program. We have selected the "Electronics" dataset and will be performing the ETL process to extract the dataset, transform the data, connect to an AWS RDS instane, and load the transformed data into pgAdmin. In addition, we will use PySpark, Pandas, or SQL to determine if there is any bias toward favorable reviews from Vine members.

## Results
The dataset had over 3 million reviews recorded. In order to focus on reviews that would be considered more likely to be helpful, we needed to filter the dataset by:
* Count of Total Votes equal or greater than 20.
* Percent of Helpful Votes to Total Votes equal or greater than 50%.

![DataGreater20_50](https://user-images.githubusercontent.com/92230478/152665365-a149dfb2-5112-4bbf-8ad5-a77bf8ee1db0.png)
The results reduced the total number of reviews from 3M to 50.7K. This allowed us to answer the following questions:
* **Vine** members made up only 2.1% (1,080) of the reviews whereas the remaining 97.9% were **Non-Vine** members (49,659).
![VineNonVineTotal](https://user-images.githubusercontent.com/92230478/152665394-d5b65f66-1383-4a16-a377-7fa6445e9529.png)
![Vine](https://user-images.githubusercontent.com/92230478/152665386-1c4c78c0-50c2-4aa9-aafb-a2fc48d5145c.png)
![NonVine](https://user-images.githubusercontent.com/92230478/152665387-b9605e87-17c5-433c-bf3d-1f2094cedf55.png)
* **Vine** members gave 454 out of 1,080 reviews a 5 star rating and **Non-Vine** members gave 23,034 out of 49,659 reviews a 5 star rating.
* 42% of the reviews for **Vine** members were rated 5 stars and 46.4% of the reviews for **Non-Vine** members were rated 5 stars.
## Summary
Based on the results, **Vine** members did not show bias when rating their products considering that the number of 5-star ratings was about 10% less than **Non-Vine** members (42% vs. 46.4%). With this, we can assume that Vine customers are more critical when submitting their review. However, in order to support this assumption further, we should include all of the data rather than filtering it to a percentage of helpful vs. total votes as we did for this analysis. Reviewing the data as is would give us more information and allow us to further support our assumption as shown below.
![nonfilteredtotal](https://user-images.githubusercontent.com/92230478/152665459-63eb131c-fccb-4f28-941b-e3577675b348.png)

In addition, running the same analysis using datasets from different product categories can provide us with the whole picture of whether reviews made by Vine members are bias.
