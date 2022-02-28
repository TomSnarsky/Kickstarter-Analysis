# Kickstarting with Excel

## Overview of Project

In this project, we performed an analysis on Kickstarter data from over 4000 campaigns in order to discern trends the understanding of which could support a playwright in launching a campaign to support a new play. Our client is a playwright seeking the best possible outcome for her Kickstarter campaign, and has sought our services in order to understand better what patterns can be found in the existing data on Kickstarter campaigns in the theater category and "plays" subcategory. 

### Purpose

The goal of our analysis was to identify salient common features across successful campaigns that were similar to our client's. This analysis was pursuant to preliminary analysis conducted on goal funding amounts and a few other parameters, along with an exploratory/preliminary market analysis for a possible UK musical; after the preliminary analysis, the analysis in this project focused on identifying patterns with respect to outcomes vs. goal amounts as well as outcomes vs. launch dates. Our analysis will conclude with actionable feedback for our client in terms of a) the funding target and b) an ideal launch window for the campaign.

## Analysis and Challenges

Below we will walk the reader through the two principal vectors of analysis we pursued: outcomes vs. goal amounts as well as outcomes vs. launch dates.

### Analysis of Outcomes Based on Launch Date

First we considered the relationship between the outcomes of campaigns for plays and their launch date. In order to conduct this analysis, we constructed a pivot table in Excel which summarized the number of successful, failed, and canceled campaigns in the theater category by the month during which they were launched. We organized the pivot table using the following labeling system:

<img width="301" alt="image" src="https://user-images.githubusercontent.com/99628051/155910640-5736f4e3-c072-40ad-aa9e-023a89e81870.png">

Once organized in a pivot table, the data could also be filtered by year, using a filter on the pivot table, as pictured below.

<img width="325" alt="image" src="https://user-images.githubusercontent.com/99628051/155910280-cf3fd990-b8dc-492a-994a-6060cd557fc6.png">

From this pivot table we constructed a line graph which represented Theater Outcomes based on Launch Date, as pictured below. The x-axis of the line graph represents the month during which the campaign was launched, and the y-axis represents the campaign count; each of the three differently-colored lines represents one kind of campaign we wanted to track in our analysis: successful, failed, and canceled.

![image](https://user-images.githubusercontent.com/99628051/155910216-cf610084-dcfc-48a9-8063-fc072a1cf4c8.png)

This data representation pointed us in a very clear direction with regards to how we advised our client about when to start the campaign in support of her play, as we discuss in the Results section below.

### Analysis of Outcomes Based on Goals

After the outcomes vs. launch date analysis we considered the relationship between the outcome of a campaign and its stated funding goal. The analysis for this portion was more complex and required us to sort the data in a new way, by creating intervals for classifying different levels of goal funding and then tracking *how many* campaigns of each kind (successful, failed, canceled) there were along with *what percentage* of campaigns fell into each category by subinterval. The raw data under our new classification is pictured below:

<img width="1309" alt="image" src="https://user-images.githubusercontent.com/99628051/155910857-bf2d927f-1f5c-47ce-892c-bd8f48db7f47.png">

Populating this worksheet required the use of a few different Excel features in our analysis, including the COUNTIFS function for the "Number" columns:

<img width="748" alt="image" src="https://user-images.githubusercontent.com/99628051/155910913-12584cf5-6321-4300-8aa2-6547d509a885.png">

We also needed the SUM function to recover the total number of projects at each goal level:

<img width="745" alt="image" src="https://user-images.githubusercontent.com/99628051/155910976-ef4ae4f9-05f5-4da6-a7ad-20db4f7cd872.png">

And last but not least, we needed the ROUND function to convert our count findings into percentages:

<img width="1330" alt="image" src="https://user-images.githubusercontent.com/99628051/155911026-3bd90008-2154-47af-a65b-39d42ee61c91.png">

These new functions led to a few challenges, as outlined in the *Challenges and Difficulties Encountered* section below.

Challenges notwithstanding, once this data was in place we were able to create a line chart for Outcomes based on Goal, as shown below:

![image](https://user-images.githubusercontent.com/99628051/155911134-fecd3a06-b167-4df7-bd04-fff4bfe34081.png)

The x-axis of this line chart is populated with the subintervals into which we split the Goal levels, and the y-axis represents the percent of campaigns (so the sum of any vertical "slice" of the graph should be 100%). The reader will notice immediately that there were 0 canceled campaigns analyzed in the dataset, a contingent fact we discuss further in the *Results* section below.

### Challenges and Difficulties Encountered

The second component of our analysis, connecting the outcome of a campaign with its funding goal, created the most difficulties. We will outline two challenges that came up during this portion of the analysis. The first challenge came with trying to efficiently use the COUNTIFS function in order to populate our "Number" columns (Number Successful, Number Failed, etc.) -- once we set all of our conditions for the COUNTIFS function, we attempted to modularize our analytical process by copying and pasting the function call from column B of our worksheet to columns C and D; unfortunately, we forgot to fix our references to columns in the Kickstarter data worksheet using the *$* symbol where appropriate, so initially this produced a whole slew of zeros instead of meaningful data. A few minutes of retyping *$*'s into the appropriate places in column B (i.e. before every mention of columns D, F, and R in the Kickstarter data sheet) and we were good to go.

Another challenge arose with the Percentage columns (Percentage Successful, Percentage Failed, etc.) -- our initial impulse was to populate this column by dividing the appropriate Number column by the Total column, *and then multiply by 100*; that, however, made it so our eventually-constructed line graph lacked the "%" labeling on the y-axis which makes the graph more readable. At first we tried to remedy this by converting all of our "Percentage" columns to percentage formatting via the home screen, but this created a different problem: now cell F2 said "7600%" instead of "76%" because changing the formatting multiplied by 100 again! Similarly to the first error, we went through and deleted the initial multiplications by 100 in column F, and then we were able to copy our formula to G and H.

## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?

The first conclusion we can draw from the Outcomes based on Launch Date data is that the highest number of successful theater campaigns are launched in May. This indicates that our client would do well to follow this trend and launch her campaign in May if at all possible. A second conclusion we can draw is that the absolute lowest number of successful theater campaigns are launched in December. This indicates that even if our client is unable to launch her campaign during the absolute peak month of May, at the very least she should certainly avoid launching her campaign in December.

- What can you conclude about the Outcomes based on Goals?

The Outcomes based on Goals data had a few interesting features: first, it showed that by raw count alone, the goal funding interval that had the highest number of successful projects was between $1000 and $4999; this supported a fact we found when we were analyzing summary statistics for the campaigns, that both measures of center for theater projects in terms of their goal amount were in the $3000-$5000 neighborhood. Unfortunately, the goal interval of $1000 to $4999 also had the highest number of *failed* campaigns, so we needed a more granular analysis to draw an appropriate conclusion. Looking at the percentages of outcomes based on goals (coupled with the simplifying fact that there were no canceled campaigns in this category), it was revealed that actually the very lowest goal funding interval, campaigns with goals below $1000, had the highest success rate by percentage, with the aforementioned $1000-$4999 category a close second. While this makes intuitive sense -- naturally campaigns with modest goals seem, a priori, more likely to be funded successfully -- the data also held an interesting surprise: two much higher funding intervals, representing goal ranges from about $35000 to $45000, achieved a 67% successful funding rate. This gave us pause in that it tells a more complicated story than some simple maxim like "the less you ask for, the more likely you are to have a successful campaign"; although those ambitious campaigns were fewer in number, they were funded at a rate only 6-9% less successffull overall than their humbler $0-$5000 counterparts! In sum, we can cautiosuly conclude that the most successful campaigns did have goals at the level of $5000 or lower, but that those categories did not have a monopoly on majority-successful campaigns by percentage (since the categories representing $35000 to $45000 also had an above-50% success rate).

- What are some limitations of this dataset?

One limitation of this dataset is something we thought, at first, was an error; as is evident from column H of our Outcomes Based on Goals sheet, there are 0 canceled campaigns in the plays subcategory represented in the dataset. This means we cannot understand the behavior of these canceled campaigns from this dataset alone, and unfortunately this gives us very little insight on what kinds of campaigns tended to be canceled and for what reasons.

Another limitation of this dataset is that the campaigns included in it only go up to the year 2017. This means that we have no data that grapples with the complexities of theater funding in the COVID era, and we are unable to perform any analyses on parameters that might only be made relevant in a COVID world (e.g. does the campaign mention socially-distanced seating? How do the COVID years affect overall funding goal levels? etc.)

- What are some other possible tables and/or graphs that we could create?

There are many other possible tables and/or graphs that we could create, so we will mention only a few here. One that might be illuminating would be looking at Outcomes based on Goal for a comparable subcategory to plays, like "musical". For a different dimension to the analysis, we also think it would be interesting to look at the effect that "spotlight" and "staff pick" designations have on campaigns' success rates; it would be valuable to be able to advise our client on whether either or both of these extra classifications would be worth pursuing for her play's campaign. Lastly, and perhaps most ambitiously, we believe it would be potentially valuable to try to conduct a kind of thematic analysis across categories to see if there might be valuable information to be gleaned that way; to understand what we mean by this, consider that the blurbs for each campaign often include descriptive language about genre or time period, so it might be possible to analyze the relative success of e.g. "sci-fi" campaigns (whether they be for movies, plays, video games, etc.) vs. campaigns for other genres. If we had information about the genre and thematic content of our client's play, this could be a useful angle to bring to our analysis.
