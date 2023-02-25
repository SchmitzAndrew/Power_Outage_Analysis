# Power Outage Characteristics In Urban and Rural Areas

## Introduction


### Our Dataset
Our dataset is information on significant power outages that took place in the continental U.S. 
The information about the power outages contains information about the region the power outages occurred, 
information about the power outage itself, and economic details from the state where the outage occurred. 

### Selected Question: Do power outages that occur in areas with high population density last longer than those that are in more sparsely populated areas?

The information in this dataset is important since it gives us a great insight into American infrastructure. This question is important because it can tell us if we are neglecting utilities' response for those in rural areas. 

The information in this dataset is important since it gives us a great insight into American infrastructure. This question is important because it can tell us if we are neglecting utilities' response for those in rural areas. 

There are 1534 rows in our dataset and 57 columns. We used a subset of those columns to answer our question.

These columns are: YEAR, MONTH, U.S._STATE, OUTAGE.START.DATE, OUTAGE.START.TIME, 
               OUTAGE.RESTORATION.DATE, OUTAGE.RESTORATION.TIME, OUTAGE.DURATION,
               POPULATION, POPPCT_URBAN, POPDEN_URBA', POPDEN_RURAL.

- YEAR: This is the year that the power outage took place
- MONTH: The month the outage took place
- U.S. State: This is the state (contintental) took place
- START.DATE: This is the date that the outage took place
- STATE.TIME: This is the time that the power outage began
- RESTORATION.DATE: This is the date that the power was turned back on and the outage ended
- RESTORATION.TIME: This is the time in the day that the power was turned back on
- DURATION: This is the time, represented as minutes, that the power outage lasted
- POPULATION: This is the population of the U.S. state that the power outage was located in. 
- POPPCT_URBAN: The percentage of residents in that state that are URBAN. The inverse of this statistic is the amount of people that are rural.
- POPDEN_URBAN: The density of those living within urban areas.
- POPDEN_RURAL: The density of those living within rural areas.
 
## Cleaning and EDA

### Data Cleaning

#### Data Cleaing Steps
We did our initial dataframe analysis in Excel, where we identified columns that might be helpful to answering our question. Then, we downloaded the file as a .csv and added the .csv file to DataLore, where we performed more data cleaning. The first thing we did was get rid of the strings that descirbed the dataset, such as the title. We then set the columns of DataFrame and selected the ones we planned on using in our analysis. Then, we fixed some of the datatypes and calculated the length of the outages by turning OUTAGE.START and OUTAGE.END into datetime objects. We then calculated the length of the outages and turned it into minutes to be similar to the OUTAGE.DUARTION column that was provided to us.
#### Head of Cleaned DataFrame

### Univariate Analysis

#### Plot Showing Distribution of Single Column
<iframe src='assets/outage-duration-histogram.html' width=800 height = 600 frameBorder=0></iframe>
#### Description of Plot
This histogram shows the distirbution of outages in our dataset. We can see that the majority of outages are very short, and there some enourmous outliers. We decided to remove the outliers:
<iframe src='assets/outage-duration-no-outliers-histogram.html' width = 800 height = 600 frameBorder=0></iframe>
After removing the outliers that are outside 2 standard deviations, we can see that not much of a difference was made to the overall distribution of outage durations. Therefore, we chose to continue using the duration with outliers since it these large outliers might still help us answer our question if they are evidence of slow repsonse times in rural areas.
### Bivariate Analysis

#### Plot Showing Relationship Between Two Columns
<iframe src='assets/duration-poppcturban-scatter-plot.html' width = 800 height = 600 frameBorder=0></iframe>

#### Interpert Plot
This plot is used to compare the data in the OUTAGE.DURATION and OUTAGE.LENGTH column and reveals that they are nearly identical. We plotted this relationship to ensure that we accurated calculated the length of the power outages since answering our question accurately depends on this value. 
### Interesting Aggregates

#### Grouped Table / Pivot Table

####  Pivot Table Interpretation
This table reveals that there is a large amount of variation between different months regarding the length of
the power outage.

## Assessment of Missingnes

### NMAR Analysis

#### State Whether There Is A Column That Is NMAR

#### Results of Missingness Permutation Tests With Respect To Data

#### Plot Related To Missingness Exploration

### Missingness Dependency

#### Present and Interperet Results of Missingness Permutation Tests

##### Embed Plot Related to Missingness

## Hypothesis Testing

### Hypothesis Testing
We are performing a Permutation Test-> Is the duration of power outages in rural areas equal to the duration of power outages in urban areas.
#### State Null and Alternative Hypotheses

#### Null Hypotheses: Whether or not the power outage occurred in a rural or urban area is not related to the duration of the power outage and any difference in this is due to chance.

#### Alternative Hypothesis: Whether or not the power outage occurred in a rural or urban area is related to the duration of the power outage and power outages in urban areas do last longer. 


#### Choice of Test Statistic

Our test statistic is the difference in means of the duration of the power outage between rural and urban outages. These accurately reflects the question we are trying to answer since it directly compares the numerical OUTAGE.DURATION columns.

#### P Value and Conclusion

We selected our p-value to be 0.05 since this is considered the industry standard and precise enough for our experiment. 

Since our p_value was much lower than our cutoff, we believe that there is an arguement to reject the null hypothesis. This leads us to believe that power outages in rural areas might last longer. However, we are not able to make a surefire statement since we are just performing statistical tests.
