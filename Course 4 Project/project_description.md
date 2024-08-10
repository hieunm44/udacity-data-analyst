# Project Overview
Introduction
Real-world data rarely comes clean. Using Python and its libraries, you will gather data from a variety of sources and in a variety of formats, assess its quality and tidiness, then clean it. This is called data wrangling. You will document your wrangling efforts in a Jupyter Notebook, plus showcase them through analyses and visualizations using Python (and its libraries) and/or SQL.

The dataset that you will be wrangling (and analyzing and visualizing) is the tweet archive of Twitter user [@dog_rates](https://twitter.com/dog_rates), also known as [WeRateDogs](https://en.wikipedia.org/wiki/WeRateDogs). WeRateDogs is a Twitter account that rates people's dogs with a humorous comment about the dog. These ratings almost always have a denominator of 10. The numerators, though? Almost always greater than 10. 11/10, 12/10, 13/10, etc. Why? Because "[they're good dogs Brent](http://knowyourmeme.com/memes/theyre-good-dogs-brent)." WeRateDogs has over 4 million followers and has received international media coverage.

WeRateDogs [downloaded their Twitter archive](https://support.twitter.com/articles/20170160) and sent it to Udacity via email exclusively for you to use in this project. This archive contains basic tweet data (tweet ID, timestamp, text, etc.) for all 5000+ of their tweets as they stood on August 1, 2017. More on this soon.
![](https://video.udacity-data.com/topher/2017/October/59dd378f_dog-rates-social/dog-rates-social.jpg)

## Project Steps Overview
Your tasks in this project are as follows:\
Step 1: Gathering data \
Step 2: Assessing data \
Step 3: Cleaning data \
Step 4: Storing data \
Step 5: Analyzing, and visualizing data \
Step 6: Reporting
* your data wrangling efforts
* your data analyses and visualizations


# Project Motivation
## Context
Your goal: wrangle WeRateDogs Twitter data to create interesting and trustworthy analyses and visualizations. The Twitter archive is great, but it only contains very basic tweet information. Additional gathering, then assessing and cleaning is required for "Wow!"-worthy analyses and visualizations.

## The Data
In this project, you will work on the following three datasets.
### 1. Enhanced Twitter Archive
The WeRateDogs Twitter archive contains basic tweet data for all 5000+ of their tweets, but not everything. One column the archive does contain though: each tweet's text, which I used to extract rating, dog name, and dog "stage" (i.e. doggo, floofer, pupper, and puppo) to make this Twitter archive "enhanced." Of the 5000+ tweets, I have filtered for tweets with ratings only (there are 2356).
![](https://video.udacity-data.com/topher/2017/October/59dd4791_screenshot-2017-10-10-18.19.36/screenshot-2017-10-10-18.19.36.png)
I extracted this data programmatically, but I didn't do a very good job. The ratings probably aren't all correct. Same goes for the dog names and probably dog stages (see below for more information on these) too. You'll need to assess and clean these columns if you want to use them for analysis and visualization.
![](https://video.udacity-data.com/topher/2017/October/59e04ceb_dogtionary-combined/dogtionary-combined.png)

### 2. Additional Data via the Twitter API
Back to the basic-ness of Twitter archives: retweet count and favorite count are two of the notable column omissions. Fortunately, this additional data can be gathered by anyone from Twitter's API. Well, "anyone" who has access to data for the 3000 most recent tweets, at least. But you, because you have the WeRateDogs Twitter archive and specifically the tweet IDs within it, can gather this data for all 5000+. And guess what? You're going to query Twitter's API to gather this valuable data.

### 3. Image Predictions File
One more cool thing: I ran every image in the WeRateDogs Twitter archive through [a neural network](https://www.youtube.com/watch?v=2-Ol7ZB0MmU) that can classify breeds of dogs*. The results: a table full of image predictions (the top three only) alongside each tweet ID, image URL, and the image number that corresponded to the most confident prediction (numbered 1 to 4 since tweets can have up to four images).
![](https://video.udacity-data.com/topher/2017/October/59dd4d2c_screenshot-2017-10-10-18.43.41/screenshot-2017-10-10-18.43.41.png)
So for the last row in that table:
* `tweet_id` is the last part of the tweet URL after "status/" → https://twitter.com/dog_rates/status/889531135344209921(opens in a new tab)
* `p1` is the algorithm's #1 prediction for the image in the tweet → golden retriever
* `p1_conf` is how confident the algorithm is in its #1 prediction → 95%
* `p1_dog` is whether or not the #1 prediction is a breed of dog → TRUE
* `p2` is the algorithm's second most likely prediction → Labrador retriever
* `p2_conf` is how confident the algorithm is in its #2 prediction → 1%
* `p2_dog` is whether or not the #2 prediction is a breed of dog → TRUE
etc.
And the #1 prediction for the image in that tweet was spot on:
![](https://video.udacity-data.com/topher/2017/October/59dd4e05_dog-pred/dog-pred.png)

So that's all fun and good. But all of this additional data will need to be gathered, assessed, and cleaned. This is where you come in.


# Step 1: Gathering Data
In this step, you will gather all three pieces of data as described below in the "Data Gathering" section in the wrangle_act.ipynb notebook.

Note: the methods required to gather each data are different.

## The WeRateDogs Twitter archive
I am giving this file to you, so imagine it as a file on hand. Download this file manually by clicking the following link: [`twitter_archive_enhanced.csv`](https://d17h27t6h515a5.cloudfront.net/topher/2017/August/59a4e958_twitter-archive-enhanced/twitter-archive-enhanced.csv). Once it is downloaded, upload it and read the data into a pandas DataFrame.

## The tweet image predictions
This file (image_predictions.tsv) is present in each tweet according to a neural network. It is hosted on Udacity's servers and should be downloaded programmatically using the [Requests](https://pypi.org/project/requests/) library and the following URL: https://d17h27t6h515a5.cloudfront.net/topher/2017/August/599fd2ad_image-predictions/image-predictions.tsv(opens in a new tab)

## Additional data from the Twitter API
Gather each tweet's retweet count and favorite ("like") count at the minimum and any additional data you find interesting. Using the tweet IDs in the WeRateDogs Twitter archive, query the Twitter API for each tweet's JSON data using Python's [Tweepy](http://www.tweepy.org/) library and store each tweet's entire set of JSON data in a file called `tweet_json.txt` file.

Each tweet's JSON data should be written to its own line. Then read this .txt file line by line into a pandas DataFrame with (at minimum) tweet ID, retweet count, and favorite count. Note: do not include your Twitter API keys, secrets, and tokens in your project submission.

__Note__: if you are not familiar with querying data from an API, you can read the next page on Twitter API, which gives a tutorial on how to Query Twitter Data.


# Additional Resource: Twitter API
## Accessing Project Data Without a Twitter Account
If you can't set up a Twitter developer account using the steps above, or you prefer not to create a Twitter account for some reason, you may instead follow the directions below to access the data necessary for the project. Note: We recommend that you follow the steps above to access the data using a Twitter developer account, because with the shortcut detailed below, you will miss practicing the valuable skill of gathering this data on your own. However, Twitter's updated process may not work for everyone, and we realize there are legitimate reasons that some students may prefer this approach, so we provide it to you here. You choose the approach to access the data that works best for you. This shortcut approach will certainly work for you to pass the project equally well.

Directions for accessing the Twitter data without actually creating a Twitter account:
At the bottom of this page you can find two files you can download:
* `twitter_api.py`: This is the Twitter API code to gather some of the required data for the project. Read the code and comments, understand how the code works, then copy and paste it into your notebook.
* `tweet_json.txt`: This is the resulting data from twitter_api.py. You can proceed with the following part of "Gathering Data for this Project" on the Project Details page: "Then read this tweet_json.txt file line by line into a pandas DataFrame with (at minimum) tweet ID, retweet count, and favorite count."


# Step 2: Assessing Data
After gathering all three pieces of data, assess them visually and programmatically for quality and tidiness issues. Detect and document at least __eight (8) quality issues__ and __two (2) tidiness issues__ in the "Accessing Data" section in the `wrangle_act.ipynb` Jupyter Notebook.

You need to use two types of assessment:
* __Visual assessment__: each piece of gathered data is displayed in the Jupyter Notebook for visual assessment purposes. Once displayed, data can additionally be assessed in an external application (e.g. Excel, text editor).
* __Programmatic assessment__: pandas' functions and/or methods are used to assess the data.
To meet specifications, the following issues must be assessed.
* You only want original ratings (no retweets) that have images. Though there are 5000+ tweets in the dataset, not all are dog ratings and some are retweets.
* Assessing and cleaning the entire dataset completely would require a lot of time, and is not necessary to practice and demonstrate your skills in data wrangling. Therefore, the requirements of this project are only to assess and clean at least 8 quality issues and at least 2 tidiness issues in this dataset.
* The fact that the rating numerators are greater than the denominators does not need to be cleaned. This [unique rating system](http://knowyourmeme.com/memes/theyre-good-dogs-brent) is a big part of the popularity of WeRateDogs.
* You do not need to gather the tweets beyond August 1st, 2017. You can, but note that you won't be able to gather the image predictions for these tweets since you don't have access to the algorithm used.
If you need some help with the datasets, you can read the page: Project Motivation.


# Step 3: Cleaning Data
Clean all of the issues you documented while assessing. Perform this cleaning in the "Cleaning Data" section in the `wrangle_act.ipynb`.

Make sure you complete the following items in this step.
* Before you perform the cleaning, you will make a copy of the original data.
* During cleaning, use the define-code-test framework and clearly document it.
* Cleaning includes merging individual pieces of data according to the rules of [tidy data](https://cran.r-project.org/web/packages/tidyr/vignettes/tidy-data.html). The result should be a high-quality and tidy master pandas DataFrame (or DataFrames, if appropriate).


# Step 4: Storing Data
In the "Storing Data" section in the `wrangle_act.ipynb` notebook, store the cleaned master DataFrame in a CSV file with the main one named `twitter_archive_master.csv`. If additional files exist because multiple tables are required for tidiness, name these files appropriately. Additionally, you may store the cleaned data in a SQLite database (which is to be submitted as well if you do).


# Step 5: Analyzing and Visualizing Data
In the Analyzing and Visualizing Data section in your `wrangle_act.ipynb` Jupyter Notebook, analyze and visualize your wrangled data.

You must produce at least __three (3) insights and one (1) visualization__.
You must clearly document the piece of assessed and cleaned (if necessary) data used to make each analysis and visualization.


# Step 6: Reporting
Create a 300-600 word written report called `wrangle_report.pdf` or `wrangle_report.html` that briefly describes your wrangling efforts. This is to be framed as an internal document.

Create a 250-word-minimum written report called `act_report.pdf` or `act_report.html` that communicates all the insights and displays the visualization(s) produced from your wrangled data. This is to be framed as an external document, like a blog post or magazine article, for example.

Both of these documents can be created in separate Jupyter Notebooks using the [Markdown functionality](http://jupyter-notebook.readthedocs.io/en/stable/examples/Notebook/Working%20With%20Markdown%20Cells.html) of Jupyter Notebooks, then downloading those notebooks as PDF files or HTML files (see image below). If you want to write a report this way, there are two Jupyter Notebook files, named "wrangle_report" and "act_report" for you in the workspace. You might prefer to use a word processor like Google Docs or Microsoft Word, however.