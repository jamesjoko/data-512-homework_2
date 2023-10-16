# data-512-homework_2
Homework 2 - Considering Bias in Data

This project aims to explore the concept of bias in data using Wikipedia articles by creating a dataset of US city Wikipedia articles along with their state populations and estimated article quality from ORES. An analysis of how the coverage of US cities' Wikipedia articles and the quality of those articles varies among states. To reproduce the analysis, run all cells in the `jjoko_data512_hw2.ipynb` notebook from top to bottom. Obtaining the revision IDs and ORES scores for articles takes a long amount of time to execute, so an intermediate dataset is located in `intermediate_data/us_cities_article_quality.csv'.

There are three source datasets:
* [Category:Lists of cities in the United States by state](https://en.wikipedia.org/wiki/Category:Lists_of_cities_in_the_United_States_by_state)
  * This was crawled to generate a list of Wikipedia article pages about US cities from each state
  * The license is located here: https://en.wikipedia.org/wiki/Wikipedia:Text_of_the_Creative_Commons_Attribution-ShareAlike_4.0_International_License
* https://www2.census.gov/programs-surveys/popest/tables/2020-2022/state/totals/NST-EST2022-POP.xlsx
  * Citation: Annual Estimates of the Resident Population for the United States, Regions, States, District of Columbia, and Puerto Rico: April 1, 2020 to July 1, 2022 (NST-EST2022-POP) Source: U.S. Census Bureau, Population Division Release Date: December 2022
* https://en.wikipedia.org/wiki/List_of_regions_of_the_United_States#Census_Bureau%E2%80%93designated_regions_and_divisions
  * This was crawled to generate a list of regional divisions for every US city
  * The license is located here: https://en.wikipedia.org/wiki/Wikipedia:Text_of_the_Creative_Commons_Attribution-ShareAlike_4.0_International_License
 
This assignment uses two APIs:
* https://www.mediawiki.org/wiki/API:Main_page
  * Used to get revision IDs
  * Terms and conditions are located here: https://www.mediawiki.org/wiki/API:REST_API#Terms_and_conditions
* https://api.wikimedia.org/wiki/Lift_Wing_API/Reference/Get_revscoring_articlequality_prediction
  * Used to get article quality prediction from revision ID
  * Terms and conditions are located here: https://foundation.wikimedia.org/wiki/Policy:Terms_of_Use

The final output files created by my code are:
* wp_scored_city_articles_by_state.csv
  * Structure: state (str), regional_division (str), population (float), article_title (str), revision_id (int), article_quality (str). 
* Tables embedded within the `jjoko_data512_hw2.ipynb` for analysis

# Research Implications
From this assignment, I learned that 
