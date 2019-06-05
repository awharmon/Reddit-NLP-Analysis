# Project 3: Using NLP to Classify Posts in /r/Creation and /r/Evolution

### Description

NLP is a powerful tool that allows us to turn text, vocabulary, and conversation into data.  This data can then be used for a number of interesting topics.  Reddit is a gathering space for individuals of all backgrounds and interests.  These interests are organized by "subreddit" and allow for a collection of posts, conversations, and comments on or related to the main topic of the subreddit.  I chose to examine posts from /r/Creation and /r/Evolution to build a classifier that may distinguish between the two.  I hoped to find interesting classifiers that are unique to each subreddit.

For project 3, the goal was two-fold:
1. Using Reddit's API, I collected posts from two subreddits.
2. I then used NLP to train a classifier to determine which subreddit a given post came from.

---

## Contents

The repository is oragnized as follows:

 - Data
     - clean_token_titles.csv
     - raw_titles.csv
 - 01_scraping.ipynb
 - 02_cleaning_tokenizing.ipynb
 - 03_EDA.ipynb
 - 04_modeling.ipynb
 - Executive_Summary.md
 - README.md
 - Requirements.txt

---

## Conclusions and Recommendations

Initially, I believed that classification of these two subreddits would have been fairly straightforward.  I believed that the topics of these two subreddits were distinct enough that there would be several strong, easily-identifiable indicators which would result in a high accuracy for classification.  However after performing this analysis, it seems that the content of the two subreddits is more blended than I initially thought.  While both subreddits deal with the same overarching origins topic, their approaches and beliefs could not be more distinct.  The blurring however seems to occur nevertheless, and based on the models and EDA there are a few reasons for this.

Primarily, while r/Evolution seems to be specifically focused within its domain, discussing topics related directly to Evolution, r/Creation seems to focus much more on comparison with its antagonist.  r/Creation included many keywords at extremely high rates that we would expect to see primarily in r/Evolution.  This resulted in a great deal of blending that made it more difficult to classify the posts.  In order to improve the model, removing the words such as 'evolution', 'dna', 'study', etc. (which one might believe to be a strong identifier of r/Evolution) from the model, may lead to more distinct categorization, improving the performance and lowering miscalssification of the models.

I also believed that, due to the subject matter, tense may have been a strong identifying feature for my models, especially for r/Evolution.  However, the analysis does not seem to suggest that this is the case.  My next step would be to copy the 3rd and 4th notebooks and rerun everything with stemmed/lemmatized words instead.  This would confirm (or refute) that tense is a non-indicator for the models.

All of the models performed significantly better than the baseline for modeling and classifying the titles.  Of the models, Multinomial Naive Bayes performed the best due to its high accuracy and relatively low overfit.  Other models, such as SVM, had higher accuracy on the training set but were significantly more overfit, and would thus not be as great of a model to use.

Given more time, I would like to follow up with my suggestions listed earlier, but more importantly, I would like to gather more data over time.  This dataset was just shy of 2000 posts, and they were all imported on the same day.  This means that the dataset was merely a snapshot of the content over the past several days (depending on the activity level of the subreddits).  Gathering at different points over several weeks would likely result in a more representative sample of each subreddit, improving the potential performance of the models.  Additionally, the posts were imported from the "Hot" subsection of each subreddit.  Because only posts with high rates of interaction show up with this section, there may be some level of confirmation bias that is not being accounted for, given that similar posts and topics are likely to be upvoted and discussed in the subreddit.  Gathering from either "Top" or "New" may help to give more representative samples.