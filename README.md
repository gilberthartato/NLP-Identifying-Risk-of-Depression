<img src="http://imgur.com/1ZcRyrc.png" style="float: left; margin: 20px; height: 55px">

# **Project 3: NLP Classification - Identifying The Risk of Depression**

>Author:  Gilbert Hartato / Han Kiong / Wee Zheng

## Context
Mental health is a growing concern in Singapore, particularly among youths, with depression being the most prevalent mental illness. The increase in depression rates among young people is largely attributed to extensive social media use, where factors like cyberbullying and the pressure to maintain a positive online image are prevalent. Considering the challenges in limiting social media usage among youths, a more viable approach is to leverage social media as a tool to identify and mitigate the rising depression rates, thereby offering better support to those in need.

## Problem Statement

This project is focused on addressing the critical question: **How can we detect if youths are at risk of depression based on their online posts?**. The primary goal is to develop a predictive model that identifies whether a youth is at risk of depression by analyzing their social media activity. 


## Data Dictionary


|Feature|Type|Dataset|Description|
|---|---|---|---|
|id|*str*|depression_happy_processed|Unique ID for each post|
|author|*str*|depression_happy_processed|Represents the username of the post owner|
|score|*integer*|depression_happy_processed|The post number of posts upvotes minus downvotes|
|total comment|*float*|depression_happy_processed|Total number of comments on the reddit post |
|created_utc|*integer*|depression_happy_processed|The time stamp when the post is created in UNIX time form|
|subteddit|*str*|depression_happy_processed|Name of the subreddit where the post is extracted|
|title_and_body|*str*|depression_happy_processed|Content of the post|
|tokenize|*str*|depression_happy_processed|List of tokenized words from title_and_body|
|lemmatized|*str*|depression_happy_processed|List of lemmatized words|
|stemmed|*str*|depression_happy_processed|List of stemmed words|


## Classification Model

**Metrics to be measured** : `recall`
The focus is on minimizing the error of predicting that a user is not at risk when they are actually at risk of depression.

**Summary of hypertuned models `accuracy` score**

||Naive Bayes|Logistics Regression|k Nearest Neighbor|
|---|---|---|---|
|CounterVectorizer|train = 0.829 <br> test = 0.795|train = 0.919 <br> test = 0.827|train = 0.965 <br> test = 0.713|
|TF-IDF|train = 0.830 <br> test = 0.789|train = 0.899 <br> test = 0.834|train = 0.772 <br> test = 0.611|

**Summary of hypertuned models `recall` score**

||Naive Bayes|Logistics Regression|k Nearest Neighbor|
|---|---|---|---|
|CounterVectorizer|train = 0.896 <br> test = 0.885|train = 0.875 <br> test = 0.783|train = 0.943 <br> test = 0.531|
|TF-IDF|train = 0.936 <br> test = 0.910|train = 0.880 <br> test = 0.824|train = 0.563 <br> test = 0.285|

The Naive Bayes model with TF-IDF appears to perform the best among the six models evaluated. It shows the smallest difference between train and test values, indicating a good fit. Additionally, this model has the highest `recall` score, making it the final model chosen for use.


## **Conclusion**

- A model is developed to identify youth at risk of depression by detecting words that indicate depressive tendencies.
- Depression is a serious and prevalent issue in our society that needs to be addressed at a young age.
- Instead of waiting for youths to seek help, our model allows for proactive identification of those at risk of depression by analyzing their language.

## Recommendations

- Social media companies can apply our predictive model to analyze posts made by youths online.
- Youths identified by our model as being at risk of depression can then be referred to support organizations, such as Care Corner or Tinkle Friend.

## Future Works

- Collaborate with the Ministry of Education (MOE) to apply our model to their database of students' termly check-in surveys, enabling schools to take proactive measures to support at-risk students.
- Integrate our model into social media platforms to function similarly to autocorrect, detecting words indicative of depression.
- Explore partnerships with search engines to make predictions based on users' search queries.
- **Model future improvements**:
  - The model may not detect words in short form or slang, which are unique to different countries. Including these slang words in our training dataset could improve its performance.
  - The model may falsely detect sarcastic posts as indicators of depression.