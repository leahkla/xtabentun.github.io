---
layout: post
title: Visualizing Twitter data with Bokeh
published: false
---

First, I made a script which merged the separate csv files (from the FiveThirtyEight dataset) into a single csv file. For these simple visualizations, I left out some of the columns from the original data: all columns with only urls were left out, a binary indicator `new_june_2018` and `harvested_date` (a column that included information on the date and time the tweet was collected by Social Studio) were also left out. Id columns `alt_external_id` and `tweet_id` were left out. `publish_date` column was converted into datetime format.

Now the `tweets` dataframe has 13 columns and 5 892 414 rows in total. If we explore only English tweets, there would be 4 233 734 tweets in the dataframe. By looking the columns of the dataframe, it would be interesting to see for example, what kind of update activity amount has the highest representation of unique handles. For observing the update activity (the number of "update actions" on the account that authored the tweet, including tweets, retweets and likes) of unique Twitter handles, I used `groupby` for `external_author_id` which will be the index and for each external author id I got a single column of list of all updates by applying lambda function to `updates` column, collecting the unique updates. Then I created a list where I collected all the maximum update values that each external author id had and visualized that as a histogram:


<iframe width="1000" height="500" frameborder="0" scrolling="no" src="../graphs/histogram_twitter_IRA.html"></iframe>

*Which bin of maximum number of update actions has the highest representation of unique Twitter handles? Are there more low activity accounts than high activity accounts in the dataset? Can we spot some interesting patterns or anomalies when it comes to update activity?*

Since the histogram has bins of 200 (from 0 to 200, 200 to 400 and so on), we'll notice that there is higher representation of low activity accounts, but also separate accounts with very high amount of update actions: the highest representation of English-tweeting unique handles (303) is around 400-600 update actions, but there are also single handles with large amount of update actions (166113). The mean of updates was 11 293 with standard deviation of 19 141. Handles that tweeted in English had over 2 million updates (2 116 867) in total.
