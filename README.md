# DSI Project 3 Web API NLP

#### For General Assembly DSI course
#### By: Goh Chun Shan, DSIF 7

---
### Project Instructions:

In week four we've learned about a few different classifiers. In week five we'll learn about webscraping, APIs, and Natural Language Processing (NLP). This project will put those skills to the test.

For project 3, your goal is two-fold:
1. Using [Pushshift's](https://github.com/pushshift/api) API, you'll collect posts from two subreddits of your choosing.
2. You'll then use NLP to train a classifier on which subreddit a given post came from. This is a binary classification problem.

#### About the API

Pushshift's API is fairly straightforward. For example, if I want the posts from [`/r/boardgames`](https://www.reddit.com/r/boardgames), all I have to do is use the following url: https://api.pushshift.io/reddit/search/submission?subreddit=boardgames. A primer video on how to use the API: https://youtu.be/AcrjEWsMi_E

---
### Introduction:

Reddit is a social news, content, and discussions website. Posts are organised according to subject into user-created 'subreddits', which covers practically any topic imaginable. Members submit content (such as images, texts, and links) to subreddits, which can then be voted up ('upvote') or down ('downvote') by other members.

The two subreddits that I have chosen for this project are: **Social Anxiety** & **OCD** (Obsessive Compulsive Disorders). These are two distinct mental health conditions. The goal of this project is to create a classification model that predicts which subreddit a random post belongs to with the highest accuracy.

###### A) Social Anxiety
Definition: Social anxiety disorder, also called social phobia, is a long-term and overwhelming fear of social situations. It's a common problem that usually starts during the teenage years. It can be very distressing and have a big impact on your life.

###### B) Obessessive compulsive disorder
Definition: a personality disorder characterized by excessive orderliness, perfectionism, attention to details, and a need for control in relating to others.

##### Usefulness:
Awareness of mental health disorders is increasing in recent years, especially with the popularity of the theme on social media. The younger generation is more comfortable with using social media to post about their daily lives, including struggles that they have, and in severe cases it could be a cry for help when they do not know where they can seek help from. Having a model that accurately sorts posts can help in online surveillance of mental health illnesses, by picking out common combinations of keywords in posts using CountVectorizer. These users can then be pointed to the right resources.

Through this exercise, we can also raise awareness about mental health conditions for the general population and roll out campaigns to educate healthcare workers or the general public about words that differentiate mental illnesses, reduce the stigma against them, and correct any common misunderstandings about them. For e.g., one common use of the word 'OCD' is  people who like to keep their living spaces clean, which is not what the term actually means, which may drown out voices online of people seeking help as people are numbed to the over-misuse of the term.

##### Method:
In this project, I create a classification model that predicts which subreddit a random post belongs to with the highest accuracy. To identify a production model, a variety of preliminary models would be tested and evaluated based on their accuracy scores (i.e. how many correct predictions they are able to make).

##### Possible Extension of project: 
If we have an indicator of severity of the cases, we can also train a model to pick out the most severe cases, and do surveillance on social media posts on potential people who are seeking help.
----
### Data Dictionary

The combined dataset (before using feature extraction):

|Feature|Type|Description|
|---|---|---|
|**subreddit**|*str*|which subreddit each post originates from| 
|**title**|*str*|title of each reddit post|
|**selftext**|*str*|text of each reddit post|
|**fulltext**|*str*|combination of title and text of each reddit post|
|**id**|*str*|created user id|

---

### Model Tuning and Insights

**Model Comparison**

In this project, we compared 2 models, Random Forest and Naive Bayes to find the best performing model. GridSearch was used to tune the hyperparameters. At the end, we also swapped the CountVectorizer for TF-IDF vectorizer to see if it gives a better performance based on our chosen key metric.

**Key Metric used for model evaluation: $F_1$-score**

- The key metric we are using to evaluate the model is 'f1_score'. In this classification problem, we neither want to minimize false positives or negatives as both mental health conditions are equally important and we wish

- Instead of using 'Recall' or 'Precision', using 'f1_score' balances our false positives and false negatives. As either false positives or false negatives increase, the denominator increases while the numerator stays fixed, meaning our $F_1$-score decreases.



|Model No.|Model Classifier|Vectorizer|Normalisation|train F1-score|test F1-score|
|---|---|---|---|---|---|
|1|Random Forest|CountVectorizer|Tokenize|0.998|0.889|
|2|Random Forest|CountVectorizer|Lemmatize|0.998|0.886|
|3|Random Forest|CountVectorizer|Stemming|0.998|0.898|
|4|Naive Bayes|CountVectorizer|Tokenize|0.998|0.888|
|5|Naive Bayes|CountVectorizer|Lemmatize|0.998|0.888|
|6|Naive Bayes|CountVectorizer|Stemming|0.999|0.897|

The best performing model was model 3, Random Forest using stemming, with a test F1-score of 0.898. All models had similar and high

Switching out the Vectorizer from CountVectorizer to TF-IDF Vectorizer (model 3, Random Forest using stemming) reaped a slightly improved result.

|Model No.|Model|Vectorizer|Normalisation|train F1-score|test F1-score|
|---|---|---|---|---|---|
|3a|Random Forest|TF-IDF|Stemming|0.999|0.901|

Hence, this was chosen as our final model for deployment.

Confusion matrix:
|Confusion matrix|Predicted r/Social Anxiety|Predicted r/OCD|
|---|---|---|
|Actual r/Social Anxiety|2706|264|
|Actual r/OCD|319|2651|

We observe that the false positives and false negatives are quite balanced without an imbalanced swing towards either Type I or Type II error.

---
### Final Conclusions and Recommendations

**Conclusions**
We noticed that all model performances were quite similar in terms of the key metric, F1 score. There is evidence of overfitting as the train score for all the 6 base models were close to 1.00 to begin with. 

Through this project, it shows that it is possible to differentiate between social media posts about different mental health conditions with high accuracy. 

**Recommendations**
Other models (aside from Random Forest and Naive Bayes, e.g. Logistic Regression, KNN) can be evaluated to see whether they can better classify posts from the subreddits related to mental health conditions to a higher accuracy.


