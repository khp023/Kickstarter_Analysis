# Kickstarting with Excel

## Overview of Project

The initiative following Louise's desire to set up her own kickstarter campaign led to the data organization and analysis of an Excel database containing global historical Kickstarters' attributes and outcomes from 2009 to 2017. The given main data set is in [Kickstarter_Challenge.xlsx](/Kickstarter_Challenge.xlsx) under the sheet titled "Kickstarter"

### Purpose

This specific analysis of the Kickstarter dataset is to trend global outcomes on Kickstarters for plays based on their launch date and goals. This information will help Louise compare her campaign results to see if they were as expected and will potentially give information on how to set up for the best outcome possible in the future. The analysis is able to demonstrate to Louise forms of data parsing from the main Kickstarter sheet and the usage of Pivot tables. 

## Analysis and Challenges

### Analysis of Outcomes Based on Launch Date

The analysis of outcomes based on launch date began with the given information of the Unix timestamp data in Column J (launched_at) in sheet titled "Kickstarter" in [Kickstarter_Challenge.xlsx](/Kickstarter_Challenge.xlsx). The timestamp was converted using `=(((J2/60)/60)/24)+DATE(1970,1,1)` in Column S (Date Created Conversion) and subsequently converted to the Year in Column U (Year Created) using `=YEAR(S2)`

The following parameters were used in the Pivot table to then portray monthly counts of each type of outcome (success, fail, cancel): 

![Pivot Chart Parameters](/resources/Theater_Outcomes_Pivot_Parameters.png)

Creating the pivot line chart resulted in: 

![Theater Outcomes vs Launch](/resources/Theater_Outcomes_vs_Launch.png)

### Analysis of Outcomes Based on Goals

The analysis of outcomes based on goals required bucketing specific ranges of prices. With the recommendation to separate the goals based on ranges of $5000, the COUNTIFS function of Excel was used to determine the number of successes, fails, and canceled campaigns based on the desired scope as follows: 
`=COUNTIFS(Kickstarter!$F:$F, "successful", Kickstarter!$D:$D, ">=1000", Kickstarter!$D:$D, "<=4999",Kickstarter!$R:$R,"plays")`

Totaling the number of campaigns at each outcome category using `=SUM(B2:D2)` allowed for the percentage calculation `=B2/E2` (formatted as percentage) for the following line chart to be created: 

![Outcomes vs Goals](/resources/Outcomes_vs_Goals.png)

### Challenges and Difficulties Encountered

Potential challenges that can come from this analysis is understanding the scope of what was desired. The initial set-up for the analysis of outcomes based on launch date failed to include the subcategory of "plays" in the countifs, resulting in an inaccurate portrayal of the specific data. In application it is reflective of the importance in the consultation process of what the client or consumer wants and checking the output/data handling if it properly shows the desired.

## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?

Based on the launch date, we can make the correlation that theater campaigns launched in May throughout the years of 2009 to 2017 have had the highest count of successes. A potential recommendation based on this information could be made to have this type of campaign during the higher success-rate months of May-July. 

However, with the peaks seen in the graph, it also indicates that most theater campaigns start during those months regardless of outcome, which may potentially indicate additional competition. 

- What can you conclude about the Outcomes based on Goals?

Per the outcomes based on goals analysis, we discover that there is no definitive linear trend from low to high, but identified maxes in success at the low ranges `< $4999` and specifically the range `$35000 - $44999`. The higher ranges beyond $44999 exhibit the most percentage failures.

- What are some limitations of this dataset?

A potential limitation of this dataset could be consumer information; everything portrayed shows the campaign-side information but lacks data on perhaps demographic or specific region (within the countries) of the kickstarters. For example a reality TV show on Beijing (cell B12) may attract an audience from that region which may skew the sampling or success rate. 

- What are some other possible tables and/or graphs that we could create?

For the theater outcomes based on launch date graph, it could instead be set up as a stacked bar graph in order to better portray the number of successes in respect to the total amount in those months. 
