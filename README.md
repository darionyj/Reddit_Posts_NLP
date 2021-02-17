# Reddit Posts NLP - Nvidia VS AMD 

## Executive Summary
As time passes, technology advances. It is very common for a person to own more than one electronic devices, such as phones, tablets or computers. There are many components in a device, such as CPU, GPU, Ram and Motherboard. Using the components, a simple device is able to display graphics and produce sound.

However, basic might not be enough for everyone. Nowadays, graphics are getting more demanding. Games is one of the factor that demand for high graphics. Latest games such as CyberPunk 2077, GTA V, Red Dead Redemption 2 and Resident Evil 3(Remake), are all graphically demanding. They can actually be played at 4K resolution with ultra texture quality which will consume alot of video memory. This is where GPU comes into play.

Currently, there is a number of companies designs and manufactures GPUs. The two major companies are Nvidia and AMD.

## Problem Statement
We will be studying the trends in the GPU markets between Nvidia and AMD. With these data and analysis, they can assist potential stakeholders such as Nvidia and AMD themselves, other GPU manufacturers, computer brands such as Dell or Asus, computer components distributors and the end-consumer. Using these data, they can make business decisions on their products, target market, pricing and availability.

We will be building classification models to study the data. The data analyzed will be based on the AMD's and Nvidia's subreddits.

In this project, there are a total of four notebooks.
1) Main Notebook - Main Notebook for Data Cleaning, EDA and Modeling
2) AMD Scrapping - For Webscrapping of AMD subreddit
3) Nvidia Scrapping - For Webscrapping Nvidia subreddit
4) Test Data Scrapping - For Webscrapping of Raw Test Data

## Contents:

1. [Datasets Used](#1-Datasets-Used)
2. [Data Dictionary](#2-Data-Dictionary)
3. [Data Collection](#3-Data-Collection)
4. [Exploratory Data Analysis & Data Cleaning](#4-Exploratory-Data-Analysis-&-Data-Cleaning)
5. [Modeling](#5-Modeling)
6. [Evaluation and Conceptual Understanding](#6-Evaluation-and-Conceptual-Understanding)
7. [Additional Testing](#7-Additional-Testing)
8. [Conclusion and Recommendations](#8-Conclusion-and-Recommendations)
9. [Python Library Used](#9-Python-Library-Used)

### 1. Datasets Used
The following datasets were created and used during this project:
- new_nvidia_posts 
- main_nvidia_posts
- rising_nvidia_posts
- today_top_nvidia_posts
- new_amd_posts
- main_amd_posts
- rising_amd_posts
- today_top_amd_posts
- nvi_combine
- amd_combine
- final_df
- amdtest
- nvitest

### 2. Data Dictionary
Below is the data dictionary containing all the data features used in different parts of the project:

|Feature|Type|Description|  
|:---:|:---:|:---:|
|subreddit|string/int|Subreddit(Nvidia or AMD)/Turns into integer after binarizing|
|selftext|string|Content in each posts|  
|title|string|Title of each posts|
|word length|float|Length of title|
|text|string|Combined selftext and title|  
|cleaned_text|string|Text after cleaning|  
|predictions|int|Predictions Outcome|  
|0|float|Probability of AMD posts| 
|1|float|Probaility of Nvidia posts|
|word|string|Individual Word|
|coef|float|Coefficient of Words|

### 3. Data Collection
Data is collected by webscrapping subreddits of Nvidia and AMD. Four different data are scrapped from each subreddit. Four different data is based on four different views in Reddit; New, Hot, Rising and Today's Top.
After scrapping, data are combined within its subreddit. Duplicated title posts were dropped. Null values posts were dropped too, as null values are posts without text. All columns were dropped except for title,selftext and subreddit.

### 4. Exploratory Data Analysis & Data Cleaning
In this section,we undergo the studying and understanding of the Nvidia's and AMD's datasets. The following are the actions taken:
 - Analyzing the distribution of posts for each subreddit
 - Combined both subreddits data together for further analyzing. Dropped duplicated title posts.
 - Did up Word Cloud to have better visual of words in both subreddit
 - Data-cleaning. Removal of certain words, stopwords and non-text characters. Lemmatizing remaining words. 
 - Visualizing cleaned data. Using count and tfidf vectorizer to explore token counts in both subreddit. Plotting top 20 words in a bar chart for each vectorizer and each subreddit. 
 
### 5. Modeling 
In this section, we built our model based on the train data. The core process will be GridSearching over hyperparameters. We will be setting up six different pipelines as followed:
- Count Vectorizer and Logistic Regression
- Count Vectorizer and Naive Bayes Classifier
- Count Vectorizer and Random Forest Classifier
- Tdidf Vectorizer and Logistic Regression
- Tdidf Vectorizer and Naive Bayes Classifier
- Tdidf Vectorizer and Random Forest Classifier

### 6. Evaluation and Conceptual Understanding
After comparing the six models using accuracy score and confusion matrix outcome, we will be using Count Vectorizer and Logistic Regression. 
Then, predictions were made to the original cleaned data. Further analysis is done to the predictions:
- Metrics Analysis
- Confusion Matrix Analysis
- Correct Predictions Analysis by looking at the posts that are predicted correctly
- Wrong Predictions Analysis by looking at the posts that are predicted wrongly. Plotting top 20 words in wrongly predicted posts to find the similarities.
- Further Study on Coefficients of the Posts

### 7. Additional Testing
We have decided to do this additional testing using the data on 4th December 2020 which is five days of difference from the original. Data will be combined and cleaned the same method.
Results turned out to be better than the original model. This proved that the model is consistent.

### 8. Conclusion and Recommendations
Creating count vectorizer and logistic regression as a pipeline then using gridsearch, this model is able to classify an unlabelled post into Nvidia or AMD with a reasonable accuracy of 81%. It also has a ROC AUC score of 82%. This has shown that AMD and Nvidia are very similar. 
Looking at the posts in both subreddits, most of them are covering a similar range of topics. From the parts of a custom-built PC, compatibility, games, availability, pricing, performance and etc.. These are not surprising as due to the fact whereby both are computer parts manufacturers which share a common goal. 
Unfortunately, this model might not be able to work well after a year. This is due to the fast advancement of technology. Every year, different manufacturers release latest GPU parts to meet the market requirements. Now we have 4K video games, next it can be 8K or even 12K. Games are not the only one which require GPU. Other usages of GPU include creative production and artificial intelligence.
To keep up with technology, a different model might have to be trained and built each year. Beside these two sub reddits, other sources to improve this model can be PC Gamer or Tech Radar.

Areas for expansion and further exploration for model:

- Use SVM for Classification
- Look at the timing of the posts 
- Look for correlation between post content

### 9. Python Library Used
- Numpy
- Pandas
- MatplotLib
- Seaborn
- Sklearn
- Request
- Nltk
- WordCloud
- PIL
- Re
- Time
- Random
