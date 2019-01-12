---
layout: post
title: Visualizing Twitter data with Bokeh
---

First, I made a script which merged the separate csv files (from the FiveThirtyEight dataset) into a single csv file. For these simple visualizations, I left out some of the columns from the original data: all columns with only urls were left out, a binary indicator `new_june_2018` and `harvested_date` (a column that included information on the date and time the tweet was collected by Social Studio) were also left out. Id columns `alt_external_id` and `tweet_id` were left out. `publish_date` column was converted into datetime format.

Now the `tweets` dataframe has 13 columns and 5 892 414 rows in total. If we explore only English tweets, there would be 4 233 734 tweets in the dataframe.


<iframe name="Histogram of update activity for unique Twitter handles who tweeted in English" width="1100" height="600" frameborder="0" scrolling="no" src="../graphs/histogram_twitter_IRA.html"></iframe>

*Which bin of maximum number of update actions has the highest representation of unique Twitter handles? Are there more low activity accounts than high activity accounts in the dataset? Can we spot some interesting patterns or anomalies when it comes to update activity?*

Since the histogram has bins of 200 (from 0 to 200, 200 to 400 and so on), we'll notice that there is higher representation of low activity accounts, but also separate accounts with very high amount of update actions:
