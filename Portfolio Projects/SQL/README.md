# Exploring Crime Patterns in Chicago

This project analyses Chicago crime data using SQL and Python. It integrates datasets related to crime statistics, census data, and law enforcement to uncover insights and trends.

Three datasets are used in this analysis:

- **Socioeconomic Indicators:** in Chicago: six socioeconomic indicators of public health significance and a “hardship index,”.
- **Chicago Public Schools:**  all school level performance data used to create CPS School Report Cards for the 2011-2012 school year
- **Chicago Crime Data:** reflects reported incidents of crime

More details and links to these datasets are given within the code. Please refer to it for more information on the dataset.
The datasets were downloaded locally and then further analysis was carried out for simplicity and ease.

## Technologies used:

- `ipython-sql`
- `prettytable`
- `pandas`
- `sqlite3`

The dependencies were installed using `!pip install ipython-sql prettytable pandas`.

**Database connection:** Establishes a connection to `FinalDB.db` using `SQLite`.

## Functions and SQL Commands Used:

- `sqlite3.connect()` → Connects to the SQLite database.
-	`PRAGMA_TABLE_INFO(table_name)` → Retrieves metadata about database tables.
-	`SELECT COUNT(*) FROM table_name` → Counts total records in a table.
-	`GROUP BY` → Used for aggregating crime statistics by category, year, and location.
-	`JOIN` → Merges datasets to analyze crime in relation to census and school data.
-	`ORDER BY`→ Sorts query results for better insights.
-	`LIMIT` → Restricts the number of results returned for readability.

## Analysis 

- Estimated total number of crimes recorded in the crime table using `PRAGMA_TABLE_INFO`.

- Identification of vulnerable regions by extracting regions  with per capita income less than 11000. 

- Regions with crime against minors by passing clause of `LIKE %MINOR%` as description.

- Further extending my analysis towards children, any kidnapping related to child abduction was analysed by passing `KIDNAPPING` as the clause type from column `PRIMARY_TYPE` which lists the types of crimes. 

- School shooting have become very common in certain parts of the world. For this, all cases which have occurred in the vicinity of schools have been highlighted passing `LIKE %SCHOOL%` clause for the column `LOCATION_DESCRIPTION` which contains the locations of the occurrence of crime. 

- `GROUP BY` was used to look  at the safety score of each school level. 

- From `CENSUS DATA` 5 communities living below poverty line have been highlighted using `LIMIT` clause.

- Finally the community being most prone to crime was identified. Case numbers were counted against each community area number to calculate a separate parameter called `FREQUENCY` for the number of  crimes in an area using `GROUP BY COMMUNITY_AREA_NUMBER` clause. Then the community area number with highest `FREQUENCY` was sorted using ` ORDER BY FREQUENCY DESC`.

## Results

The analysis of crime data in Chicago, spanning from 2001 to the present, reveals a total of 533 registered crimes. Notably, regions such as South Lawndale, Fuller Park, West Garfield Park, and Riverdale are identified as the most vulnerable areas, with a potential correlation between lower income levels and increased susceptibility to crime due to limited access to proper living conditions. 

Among the recorded incidents, there are two cases involving minors, both linked to illegal substance consumption, and one case concerning the kidnapping of a child. Additionally, 12 crime-related incidents have been reported near school zones, with middle schools having the lowest safety ratings compared to elementary and high schools.

Communities such as Rogers Park, West Ridge, Uptown, Lincoln Square, and North Center are identified as areas with significant portions of the population living below the poverty line, with North Center having the lowest **Hardship Index** of 6.0. Of particular concern is the community of Austin (Community Number 25), which has the highest rate of criminal occurrences in the city.

Moving forward, a more detailed investigation into crime patterns in Austin could provide valuable insights into the specific areas with the highest crime rates, allowing for more targeted intervention. Additionally, there is a critical need for increased protection and public awareness regarding personal safety in lower-income neighborhoods, which are especially vulnerable to criminal activity. Schools in proximity to crime incidents should be prioritized for enhanced security measures and thorough assessments to mitigate the occurrence of future crimes in these areas.

### To be noted
The whole analysis can be performed using SQL server. This project provides a structured approach to analysing Chicago crime data, using both SQL and Python for data handling and insights extraction.
