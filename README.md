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
When performing the analysis for this assignment, I found that states with relatively low populations like Vermont, North Dakota, and Maine had higher total coverage. In fact, the 5 states with the lowest populations in the census data (excluding D.C. because it was not in the Wikipedia article dataset) were in the top 10 highest total coverage list. This makes sense because the density of the cities within those states is much lower compared to other states. The exception to this was Pennsylvania and Michigan. I theorize these states did not follow the trend because they have many cities relative to their populations. Pennsylvania and Michigan are top 2 in the number of articles in the Wikipedia articles dataset. In terms of low coverage, states like North Carolina, Nevada, and California had the worst total coverage. By definition of coverage, these states are likely a combination of a low number of cities (like Nevada) with high population density (like California). Some states with the largest populations were on the top 10 lowest coverage list like California, Florida, and North Carolina. Otherwise, it was states with fewer cities and less population density.

For high-quality articles, I once again found that the states with a high ratio of high-quality articles per capita were states with lower populations. The exception is Pennsylvania again and New Jersey. I theorize that both states have a high number of quality articles because the states have high historical significance. Also, pages with high historical significance may be less likely to be changed frequently. The states with the lowest ratios also tended to be states with high populations like California, Florida, and New York. Since we're looking at per capita, it makes sense that states with high populations tend to have the lowest ratios since the population is the denominator, even though the states with large populations might have more high-quality articles than states with small populations due to their density. One exception state is Nevada because it only has 19 cities. Generally, the pattern of high-quality article coverage was the same as total coverage. 

For divisions, I found that there wasn't a very consistent pattern between the divisions and their total coverage ratio. For example, divisions with higher populations tended to have lower total coverage like the Pacific and South Atlantic and divisions with lower populations tended to have higher total coverage like West North Central and New England. However, there exist exceptions like how East North Central has the third highest population and second highest total coverage and Mountain has the fourth lowest population yet the third lowest total coverage. For high-quality coverage, I found the same pattern of divisions with high populations having low high-quality coverage but didn't find that a lower population division led to more high-quality coverage. Generally, throughout all six tables, I found biases that states and divisions with larger populations had lower total and high-quality coverage and states and divisions with smaller populations had higher total and high-quality coverage.

Before I started working with the data, I expected to find states with larger populations to have a higher ratio of high-quality coverage. My reasoning was that articles about cities in more populous states would have a lot more eyes and editors watching them, leading to a higher standard of quality than cities in states with smaller populations. As such, I definitely expected states like New York, California, and Texas to have high high-quality coverage due to their large populations, but the exact opposite happened likely because the populations are so large that they weigh down the ratio. I also expected states with small populations to have very few articles and few high-quality articles because there wouldn't be many editors for the upkeep and documentation. I also expected historical areas like New England to have high high-quality coverage due to their historical significance to America.

A source of bias I discovered in my data analysis is that states with generally more municipalities have more total coverage by definition and are likely to have more high-quality articles because they can send more articles by volume to ORES. For example, it's hard to say that of Pennsylvania's 2556 total articles, 566 of them would be high-quality. 

I think my results suggest that Wikipedia as a data source is pretty heavily biased towards pages and areas that have a lot more editors and upkeep. Since article quality is largely based on public contribution and the experience of the editors who work on articles, using quality as a metric is largely subjective and unreliable for significant quantitative analysis.
