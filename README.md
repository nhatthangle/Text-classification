# Deep Learning Project - Text classification
By Nhat Thang LE & Emir Dakin TARIK

## Motivation 

In recent years, text classification has become a well-known topic around the world with a wide range of applications in dectecting hateful racisms, spam emails, frauds, recommendation algorithms, etc. A lot of treatments have been proposed to enhance models' performance and many different preprocessing or embedding techniques have been used for cleaning data, texts and then turning texts, sentences, words into vectors of real numbers for easier manipulation. For this reason, we are amused by it's essence and would like to do a text classification for ourselves with the aim to see how far we can improve our model accuracy using many different optimization, regularlization techniques and additionally, to see if a stemming method helps improve the test set accuracy.

## Objectives
In this project, we would like to try text classification models on a text data that gives ratings to books on Amazon website. We would like to see how much better or how much worse (in terms of test accuracy) a regularization method or an optimization method can add to our models. Another persepective is that we want to comapare different well-known ML algorithms such as Logistic Regression, Support Vector Machine, Naive Bayes etc. as well as deep neural network models.

Moreover, we would try to do a multi-classification task rather than the "traditional" binary classification task, which would be kind of boring.

## Dataset
We use a dataset that can be downloaded from this link:
https://www.kaggle.com/meetnagadia/amazon-kindle-book-review-for-sentiment-analysis?select=preprocessed_kindle_review+.csv
The dataset contains 12000 reviews of amazon kindle books with corresponding ratings taking integer values from 1 to 5. The other variables are "ID" and "summary" but we do not care about these variables. Here is a look at the distribution of ratings from 1 to 5: 

(picture of the table)

As we can see, the data is quite balanced for classification task: If we consider reviews with ratings greater than 3 stars as "good" and the rest is "not good", we will have 6000 "good" and 6000 "not good" reviews. However, as stated above, our task is to train models that classify the ratings into 5 categories corresponding to integers from 1 to 5. As a result, our task should have the accuracy (on the test set) greater than that of the "dumb model", which is 3000/12000 = 25%, in which case, it classifies all the test reviews as 5 stars (or 4 stars), supposing that the ratings of the test set have a proportionate distribution to the whole data set (that is approximately 1/6 for 1-star, 2-star, 3-star ratings nad 1/4 for 4-star and 5-star ratings).
