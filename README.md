# DSI Project 3 Web API NLP
For General Assembly DSI course
By: Goh Chun Shan, DSIF 7

### Description

In week four we've learned about a few different classifiers. In week five we'll learn about webscraping, APIs, and Natural Language Processing (NLP). This project will put those skills to the test.

For project 3, your goal is two-fold:
1. Using [Pushshift's](https://github.com/pushshift/api) API, you'll collect posts from two subreddits of your choosing.
2. You'll then use NLP to train a classifier on which subreddit a given post came from. This is a binary classification problem.

#### About the API

Pushshift's API is fairly straightforward. For example, if I want the posts from [`/r/boardgames`](https://www.reddit.com/r/boardgames), all I have to do is use the following url: https://api.pushshift.io/reddit/search/submission?subreddit=boardgames. A primer video on how to use the API: https://youtu.be/AcrjEWsMi_E


### Project Description:

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


### Exploratory Data Analysis

#### Conclusions


### Model Tuning and Insights


### Final Conclusions and Recommendations
