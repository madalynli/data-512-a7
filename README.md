# DATA 512 A7: Project Report<br>
Madalyn Li<br>
Fall 2021

# Goal
The purpose of this project is to expand on the datafication of Covid-19. Specifically, the analysis for this project will focus on acquiring insights about how Yelp consumer reviews for restaurants within Wake County, NC were impacted during the course of the pandemic. The impact of this work will bring valuable insights that can potentially help drive revenue back into the restaurant industry and help re-establish trust between consumers and restaurants by promoting a public environment in which customers feel safer and at ease. The code and steps available to reproduce the analysis is located within the Jupiter notebook in this repository named hcds-a7-project-report.

# Data Sources
This project uses data from three different sources:
1. [Restaurants in Wake County - Yelp](https://data-wake.opendata.arcgis.com/datasets/Wake::restaurants-in-wake-county-yelp/about)<br>
This file is available to download for free and the terms of use can be found [here](https://maps.wakegov.com/agso/OpenData/TermsOfUse.html). The file can also be found in the repository within the Raw Data folder and is titled *Restaurants_in_Wake_County_-_Yelp.csv*. The data includes a list of all restaurants on Yelp that are in Wake County with some additional information about these restaurants highlighted below: 

| Column | Description |
| --- | --- |
| **BUSINESS ID** | Contains a unique business id for each restaurant |
| **NAME** | Contains the name of the restaurant |
| **ADDRESS** | Contains the address of the restaurant |
| **CITY** | Contains the city of the restaurant |
| **STATE** | Contains the state of the restaurant |
| **POSTAL CODE** | Contains the zip code of the restaurant |
| **LATITUDE** | Contains the latitude coordinates of the restaurant |
| **LONGITUDE** | Contains the longitude coordinates of the restaurant |
| **PHONE NUMBER** | Contains the unique phone number of the restaurant |

2. [Yelp Fusion API](https://www.yelp.com/developers/documentation/v3)<br>
The data files from the Yelp Fusion API query can be found in the repository within the Raw Data folder. Furthermore, Yelp Fusion API’s terms of use can be found [here](https://www.yelp.com/developers/api_terms). There are two files that were queried from the API: *yelp_business_df.csv* which contains information on the restaurant and *yelp_reviews_df.csv* which contains data points on the reviews for each restaurant. Below is a brief description of the files and columns contained:<br>

a. From the *yelp_business_df.csv* which references this [endpoint documentation](https://www.yelp.com/developers/documentation/v3/business_search_phone):

| Column | Description |
| --- | --- |
| **business_id** | Unique Yelp ID of this business |
| **review_count** | Number of reviews for this business |
| **rating** | Rating for this business |
| **transactions** | A list of Yelp transactions that the business id registered for |

b. From the *yelp_reviews_df.csv* which references this [endpoint documentation](https://www.yelp.com/developers/documentation/v3/business_reviews):

| Column | Description |
| --- | --- |
| **review_id** | A unique identifier for this review |
| **rating** | Rating of this review |
| **time_created** | The time that the review was created in PST |

It is important to note that the Yelp Fusion API returns only the top three reviews of each restaurant sorted by their [default sort order](https://www.yelp-support.com/article/How-is-the-order-of-reviews-determined). Please refer to the Jupyter Notebook and the research report for details on how I handled this limitation. 

3. [COVID-19 data from John Hopkins University](https://www.kaggle.com/antgoldbloom/covid19-data-from-john-hopkins-university?select=RAW_us_confirmed_cases.csv)<br>
This file is available to download for free under a [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) license. The file can also be found in the repository within the Raw Data folder and is titled *RAW_us_confirmed_cases.csv*. The data includes information on the daily reported number of covid-19 cases in the US on a county level. The file contains a significant amount of columns listed by day that includes the case count. I will only list out the important columns used as a reference to gather daily case count data:

| Column | Description |
| --- | --- |
| **Province_State** | US state name |
| **Admin2** | US county name |

# Clean Data File
The final clean data file is located in the Clean Data folder within the repository; the file is titled *cleaned_yelp_data.csv*. The table below includes a list of all the fields in this cleaned dataset along with a short description of each.

| Column | Description |
| --- | --- |
| **business_id** | Unique Yelp ID of this business |
| **transactions** | A list of Yelp transactions that the business id registered for |
| **avg_rating** | Average of the top reviews returned for each restaurant from the Yelp Fusion API |
| **count_review** | Count of the top reviews returned for each restaurant from the Yelp Fusion API |
| **month_year** | Contains the month and year that the review was left at the restaurant |
| **pickupordelivery** | Contains ‘yes’ if the restaurant offers pickup or delivery and ‘no’ if the restaurant does not |
| **avgabove3.5star** | Contains ‘yes’ if the restaurant’s avg_rating is above 3.5 stars, and ‘no’ if the restaurant’s avg_rating is not |

# File Descriptions
Below is a table of the descriptions for each file within this repository. They are listed in a general order to follow when reproducing the analysis:

| File Name | Description |
| --- | --- |
| **Restaurants_in_Wake_County_-_Yelp.csv** | This file contains data for all restaurants on Yelp within Wake County obtained from the Wake County government site |
| **yelp_business_df.csv** | This file contains all the business information data queried from the Yelp Fusion API |
| **yelp_reviews_df.csv** | This file contains all the business reviews data queried from the Yelp Fusion API |
| **RAW_us_confirmed_cases.csv** | This file contains the daily reported covid-19 case counts in the U.S. |
| **cleaned_yelp_data.csv** | This file contains the cleaned and finalized dataset used for analysis |
| **NOV2021_data512_a6.png** | This file contains the result of the time series graph measuring monthly change in average ratings for the data obtained from the Yelp query ran in November |
| **DEC2021_data512_a6.png** | This file contains the result of the time series graph measuring monthly change in average ratings for the data obtained from the Yelp query ran in December |
| **NOV2021_data512_a6_2.png** | This file contains the result of the time series graph measuring monthly change in number of reviews for the data obtained from the Yelp query ran in November |
| **DEC2021_data512_a6_2.png** | This file contains the result of the time series graph measuring monthly change in number of reviews for the data obtained from the Yelp query ran in December |
| **NOV2021_data512_a6_3.png** | This file contains the result of the pie chart displaying the proportion of each type of restaurant calculated for the data obtained from the Yelp query ran in November |
| **DEC2021_data512_a6_3.png** | This file contains the result of the pie chart displaying the proportion of each type of restaurant calculated for the data obtained from the Yelp query ran in December |
| **hcds-a7-project-report.ipynb** | This file contains a Jupiter notebook containing all code and documentation for the analysis of this project |
| **hcds-a7-project-report.pdf** | This file contains the written final report for this project |

# Final Report
The final report file titled *hcds-a7-project-report.pdf* contains a final write-up report detailing the research, analysis, and findings for this project. Please refer to this document and read it thoroughly to understand details regarding why I chose specific methods to use, the background and motivation for this entire project, and the limitations and issues found during my analysis.

# References
1. https://www.forbes.com/sites/aliciakelso/2020/07/07/the-covid-19-crisis-will-likely-lead-to-a-massive-shakeout-in-the-restaurant-industry/?sh=5f584efb42a0
2. https://restaurant.org/nra/media/downloads/pdfs/business/covid-19-restaurant-impact-survey-september-2021.pdf
3. https://restaurants.yelp.com/articles/dine-in-vs-takeout-trends/
4. https://www.nytimes.com/2021/07/02/technology/restaurant-delivery-takeout-orders-covid-coronavirus.html
5. https://github.com/nytimes/covid-19-data/tree/master/mask-use

# Data Sources
1. https://data-wake.opendata.arcgis.com/datasets/Wake::restaurants-in-wake-county-yelp/about
2. https://www.kaggle.com/antgoldbloom/covid19-data-from-john-hopkins-university?select=RAW_us_confirmed_cases.csv
3. https://www.yelp.com/developers/documentation/v3

