# Classifiying Social Media Posts on Mental Health
***

## Introduction
***
This project examines subreddits <a href="https://www.reddit.com/r/Anxiety/" target="_blank">r/Anxiety</a> and <a href="https://www.reddit.com/r/depression/" target="_blank">r/depression</a> to figure out the textual evidence that differentiate discussions on the mental health disorders. With the ongoing global coronavirus pandemic<a href="https://covid19.who.int/region/wpro/country/sg" target="_blank"><sup>1</sup></a>, as well as political and economic crises<a href="https://www.cfr.org/report/conflicts-watch-2022" target="_blank"><sup>2</sup></a>, there is an increase in the number of people who are facing dips in their mental health. The National Population Health Survey<a href="https://www.moh.gov.sg/docs/librariesprovider5/default-document-library/nphs-2020-survey-report.pdf" target="_blank"><sup>3</sup></a> conducted during the nascence of the corona outbreak reported a decline in mental well-being of Singaporeans, with the mean score decreasing to 7.28 in 2020 from 7.4 in 2018. The study also found that only 1 in 2 were willing to seek professional consultation when they are overwhelmed by stress. Most interestingly, the survey uncovered poor mental health to be most prevalent in young people, with 21.5% of those between 18 to 29 years old surveyed facing mental health issues.

Recent research<a href="https://acamh.onlinelibrary.wiley.com/doi/abs/10.1111/jcpp.13606" target="_blank"><sup>4</sup></a> conducted to probe the global prevalence of anxiety and depression symptoms among college students and potential associated factors found that 33.6% of college students collectively experience depression and anxiety symptoms. The prevalence of symptoms for anxiety and depression respectively were found to be higher in studies conducted after the 2019 coronavirus outbreak.

## Problem Statement
***
As the data team of uniCHIP- a social networking site and news aggregator that has been newly created for local university students, we want to be able to identify posts that contain textual evidence of users' experience with anxiety and/or depression on our platform. This can be achieved by developing a classification model that can predict with over 90% accuracy and precision, which category a post belongs to. However, as we have only recently launched, we are training our model using text data collected from subreddits which are forums dedicated to the specific topic. The text data collected from the subreddits r/Anxiety and r/depression will act as proxy for the user posts uploaded to the uniVERSE forums. Hence, we will be able to train the model to direct these users towards useful and relevant community resources for the mental health issues they are facing.

## External Research
***
<a href="https://www.reddit.com" target="_blank">Reddit</a> is a social news aggregator site that is organised into niche forums called subreddits. Each subreddit is dedicated to its namesake topic. Posts that appear on a subreddit are guided by a unique set of rules, a team of moderators and an internal voting system<a href="https://nealschaffer.com/subreddit/" target="_blank"><sup>5</sup></a>. Subreddits are notated as /r/{topic}, hence, r/Anixety and r/depression refers subreddits that aggregates discussions on the respective topics.

Here are some brief notes on the subreddits from which data was scraped:

* r/Anxiety was created on created Sep 15, 2008. As of end-November 2022, the subreddit recorded 581k members. The community has officially described the r/Anxiety forum as "discussion and support for sufferers and loved ones of any anxiety disorder". 

* r/depression was created Jan 1, 2009. As of end-November 2022, the subreddit recorded 919k members. The community has officially described the r/depression forum as "peer support for anyone struggling with a depressive disorder."

Both subreddits have similar rules for submissions<a href="https://www.reddit.com/r/Anxiety/" target="_blank"><sup>6</sup></a>  <a href="https://www.reddit.com/r/depression/" target="_blank"><sup>7</sup></a>. The respective communities urged its members to submit posts relevant to the topic, provide support when responding to original posts, to take care of their 'tone', and refrain from advocating for any quick fix solutions. Both communities also frown upon solicitation of any sort. In addition, r/anxiety encourages sharing of research studies, while r/depression discourages members from making any offers/ requests/ advocacy for (or against) treatment as well as pro-self harm posts/replies.




## Executive Summary
***
In the first notebook, 30 days of Subreddit submissions data was queried and collected from Reddit using Pushshift API. Data from r/Anxiety was saved as `anxiety_data` while data from r/depression was saved as `depression_data`. Next, the raw datasets collected were joined to hold both datasets aforementioned and saved as `raw_cleaned`.

In the second notebook, data analysis was done. To achieve this, the textual data was cleaned in a few steps. Null values, posts marked as 'removed' and 'deleted' were examined and dealt with appropriately. Next, the 'title' and 'selftext' columns were also merged to form a more cohesive single column 'post' where the submitted text can be analysed more efficiently as a whole. After the cleaning phase, the datasets were saved as `anxiety_cleaned` and `depression_cleaned` respectively.

Then, the text data was pre-processed in order to aid the Natural Language Processing (NLP) analyses later. As such, punctuations were removed, and so were numbers and stopwords. The text in the 'post' column were further treated with functions 'tokenise' and 'lemmatise'. Tokenisation breaks long strings of text into words, whose relationships to each other and the subreddit label can thus be examined. Lemmatisation reduces these words further into its meaningful base form, based on its morphology. 

Exploratory data analyses conducted on each subreddit's dataset uncovered highly frequent words in each subreddit, as well as highly frequent bigrams and trigrams unique to each subreddit. There were some co-occurring words that appeared in both subreddits' highly frequent word lists. The stopword list was extended to include filler words and personal pronouns, and these were subsequently removed from the cleaned datasets. Fillers are discourse markers that are unnecessary cliches and do not offer meaning to the topic. Personal pronouns are also highly common in both datasets as submissions to the subreddits are usually based on the user's personal experience. The cleaned datasets were merged into a single dataset `combined_cleaned` and ready for analysis with NLP.

Before the word tokens in the cleaned dataset can be analysed, it has to be transformed further into vectors, which turns them into numbers that can be understood by the machine. Representing text data numerically is called count vectorization. There are a few count vectorization techniques, and in this project, CountVectorization and TF-IDF are used. In addition, CountVectorization is done on single word tokens as well as bigram tokens. 

The Classification Models trained to classify the text data are mainly Naive-Bayes Multinomial and Logistic Regression. Each model type was trained separately data that has been transformed using different techniques: CountVectorisation of word tokens, CountVectorisation of bigram tokens, and TF-IDF vectorisation. As such, six different classification models were fitted on the train data and used to derive predictions on the test data. 

In order to evalute each model's performance, the train and test scores as well as the AUC values (from the AUC-ROC plots) were considered. For this project, a successful model is defined as one with high train and test scores, with least difference between the two, as it means that the model is suitably fitted, can be generalised to new and unseen data and can accurately predict whether text belongs to positive class (r/depression). It is more important to correctly identify a post containing experiences with depression than it is to wrongly identify other posts as containing experiences with depression. 

Furthermore, an AUC that is closest to 1 marks a successful model as it means that the model has excellent capacity to distinguish between positive class (feature belongs to r/depression) and negative class (feature belongs to r/Anxiety).

## Data Dictionary
***

Datasets: `anxiety_data`, `anxiety_cleaned`

|Feature|Type| Dataset| Description|  
|:---------|----- |-----------|:--------------|  
|subreddit |string| anxiety | Labels the subreddit the posts is extracted from. Named after the topic of interest.
|title |string|anxiety|Headline of the posts submitted on the subreddit. 
|selftext |string|anxiety|Body of the posts found in the subreddit. Typically contains more details and context to the post. 
|post |string|anxiety|Formed by merging the title and selftext columns.

<br>

Datasets: `depression_data`, `depression_cleaned`

|Feature|Type| Dataset| Description|  
|:---------|----- |-----------|:--------------|  
|subreddit |string|depression| Labels the subreddit the posts is extracted from. Named after the topic of interest.
|title |string|depression|Headline of the posts submitted on the subreddit.
|selftext |string|depression|Body of the posts found in the subreddit. Typically contains more details and context to the post.  
|post |string|depression|Formed by merging the title and selftext columns.


<br>

Datasets: `raw_cleaned`, `combined_cleaned`

|Feature|Type| Dataset| Description|  
|:---------|----- |-----------|:--------------|  
|subreddit |string|raw, combined|Labels the subreddit the posts is extracted from. Named after the topic of interest.
|title |string|raw, combined|Headline of the posts submitted on the subreddit.
|selftext |string|raw, combined|Body of the posts found in the subreddit. Typically contains more details and context to the post.
|post |string|raw, combined|Formed by merging the title and selftext columns.

## Summary of Results

|Count vectorisation technique|Model type|Train score|Test score|AUC| 
|:----------------------------|:---------|:---------:|:--------:|:--:|  
|CountVectorizer |Naive-Bayes Multinomial|0.9175|0.8644|0.92|
|CountVectorizer |Logistic Regression|0.9935|0.8659|0.93|
|Bigram |Naive-Bayes Multinomial|0.9943|0.8225|0.90|
|Bigram |Logistic Regression|0.998|0.812|0.88|
|TF-IDF |Naive-Bayes Multinomial|0.9185|0.8562|0.93|
|<font color="blue">TF-IDF </font>|<font color="blue">Logistic Regression</font>|<font color="blue">0.9435</font>|<font color="blue">0.8846</font>|<font color="blue">0.95</font>|


## Conclusions
The Logistic Regression Model is the most successful classification model, with train and test scores of 0.9435 and 0.8846 respectively and AUC value of 0.95. This means that the model is best able to generalise on new text data and accurately identify a text post that contains user's experiences with depression. At the same time, as the model has highest AUC of 0.95, it can best differentiate whether a post contains user's experiences with depression or anxiety.

However, it should be noted that there are a few limitations of this model. As reddit submissions were used as proxy, textual evidence was only limited to the 30 days worth of submissions queried from each subreddit. There could be other pressing issues that plague users with anxiety or depression that were not discussed and/or not captured by the dataset. As Chippy, the app by uniCHIP is designed for local university students, there could also be a lack of representation of this demographic in the respective communities of r/Anxiety and r/depression. As such, future improvements could be made by scraping data of other university forums instead, in order to capture data more representative of our user population. Additionally, analyses were only done on unigrams, bigrams and trigrams, which may not give a full understanding of the submissions posted about the topic. We could further classify posts as user's own experience with anxiety or depression, or caregiver's experience in dealing with someone with the mental health disorder, then conduct sentiment analyses on each type of post.

In reality, there could be co-morbidity amongst users. Patients with mental health disorders can experience both anxiety and depressive symptoms. However, for this project, due to limited internal data, we work on the premise that users submit posts to the subreddit with their predominant symptoms. 


## Recommendations
The mental health illness umbrella is not limited to anxiety and depression. Thus, we can expand this project to classify other prevalent mental health issues as well. Future developments uniCHIP can make to its app, Chipper include a way to automatically identify posts containing user experiences with poor mental health concerns. 

Additionally, collaboration with local mental health resources can bolster uniCHIP's endeavors to achieve its corporate social responsibility goals. Working on a campaign with mental health helplines and national healthcare institutions will further raise awareness for mental health issues and educate users on how to identify and care for someone suffering from poor mental health.


