# Deep Learning Project - Text classification
By Nhat Thang LE & Emir Dakin TARIK

## Motivation 
<p align="justify">
In recent years, text classification has become a well-known topic around the world with a wide range of applications in dectecting hateful racisms, spam emails, frauds, recommendation algorithms, etc. A lot of treatments have been proposed to enhance models' performance and many different preprocessing or embedding techniques have been used for cleaning data, texts and then turning texts, sentences, words into vectors of real numbers for easier manipulation. For this reason, we are amused by it's essence and would like to do a text classification for ourselves with the aim to see how far we can improve our model accuracy using many different optimization, regularlization techniques and additionally, and to see if a stemming method helps improve the test set accuracy.
</p>

## Objectives
  
<p align="justify">
In this project, we would like to try text classification models on a text data that gives ratings to books on Amazon website. We would like to see how much better or how much worse (in terms of test accuracy) a regularization method or an optimization method can add to our models. Another persepective is that we want to comapare different well-known ML algorithms such as Logistic Regression, Support Vector Machine, Naive Bayes etc. as well as deep neural network models.
</p>

<p align="justify">
Additionally, we would try to do a multi-classification task rather than the "traditional" binary classification task, which would be kind of boring. Moreover, the code written in our project is original, we have consulted some extra small ideas from various pages but they are not too significant. 
</p>

## Dataset
We use a dataset that can be downloaded from this link:

https://www.kaggle.com/meetnagadia/amazon-kindle-book-review-for-sentiment-analysis?select=preprocessed_kindle_review+.csv

<p align="justify">
The dataset contains 12000 text reviews of amazon kindle books (the "reviewText" column) with corresponding ratings (the "rating" column) taking integer values from 1 to 5. The other variables are "ID" and "summary" but we do not care about these variables. The text reviews are all about how good/bad a book is rather than the physical quality of the product like in the case of printed books.
</p>

Here is a look at the distribution of ratings from 1 to 5: 

(picture of the table)

<p align="justify">
As we can see, the data is quite balanced for classification task: If we consider reviews with ratings greater than 3 stars as "good" and the rest is "not good", we will have 6000 "good" and 6000 "not good" reviews. However, as stated above, our task is to train models that classify the ratings into 5 categories corresponding to integers from 1 to 5. As a result, our task should have the accuracy (on the test set) greater than that of the "dumb model", which is 3000/12000 = 25%, and in which case, it classifies all the test reviews as 5 stars (or 4 stars). The previous statement supposes that the ratings of the test set have a similar distribution as of the whole dataset (that is, each of 1-star, 2-star, 3-star ratings accounts for approximately 1/6 of the reviews and each of 4-star and 5-star ratings accounts for 1/4 of the reviews).
</p>

First few lines of the dataset: 

(picture)

## Data cleaning
We perform data cleaning by:

•	lowercasing the words in each review \
•	removing punctuations and possibly some urls \
•	tokenzing the reviews and then removing stopwords using nltk 

<p align="justify">
Before untokenizing the reviews, we also used Snowball Stemmer to stem the words. Snowball Stemmer has become popular in recent years and has been considered as the best stemming method by some parts of Machine Learning Community. In 2021, the Snowball Team released version 2.1 and 2.2, here is their website:
  
https://snowballstem.org/
</p>

In the following analysis, we will perform classification on the cleaned data without stemming and the stemmed data to see if Snowball Stemmer helps or not.

For the classification task we will use TF-IDF representation for each review. Bag-of-words representation was considered but due to the runtime of the code, we drop this case.

## Classification Models

<p align="justify">
The first part is to try all well-known ML classifiers: 
  
•	Ensemble methods: Bagging of trees, Random Forest, Gradient Boosting, Extreme Gradient Boosting, AdaBoost, LightGBM  \
•	Support Vector Machines methods: Linear SVC and Nonlinear SVM with polynomial and Gaussian kernels \
•	Discriminant Analysis: Linear and Quadratic
  
Moreover, we also try to perform parameters tuning to enhance the performance of some of these methods, the rest takes too long to tune.
 </p>

<p align="justify">
The second part will focus on Neural Network models:
  
•	Basic Sequential models \
•	RNN models: LSTM models \
•	CNN model
  
The main focus is to try enhance model performance by adapting different optimization algorithms such as SGD (mini-batch, batch), RMSProp, Adam etc. and by imposing regularization methods such as l1, l2 regularizations, dropout, batch-normalization, early stopping, weight initilizations and combinations of them.
</p>

As has been said above, we will perform classification on both cleaned data without stemming and the stemmed data






