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

<img src="https://github.com/nhatthangle/Project-Deep-Learning---Text-classification/blob/main/ratings_distribution.png" width="450" height="300" />

<p align="justify">
As we can see, the data is quite balanced for classification task: If we consider reviews with ratings greater than 3 stars as "good" and the rest is "not good", we will have 6000 "good" and 6000 "not good" reviews. However, as stated above, our task is to train models that classify the ratings into 5 categories corresponding to integers from 1 to 5. As a result, our task should have the accuracy (on the test set) greater than that of the "dumb model", which is 3000/12000 = 25%, and in which case, it classifies all the test reviews as 5 stars (or 4 stars). The previous statement supposes that the ratings of the test set have a similar distribution as of the whole dataset (that is, each of 1-star, 2-star, 3-star ratings accounts for approximately 1/6 of the reviews and each of 4-star and 5-star ratings accounts for 1/4 of the reviews).
</p>

First few lines of the dataset: 

<img src="https://github.com/nhatthangle/Project-Deep-Learning---Text-classification/blob/main/First%20lines.png" width="1000" height="270" />

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

For the classification task we will use TF-IDF representation for each review using 1 and 2-gram words. Bag-of-words representation was considered but due to the runtime of the code, we drop this case.

<img src="https://github.com/nhatthangle/Project-Deep-Learning---Text-classification/blob/main/TF-IDF.png" width="600" height="300" />


Let's take a look at how different a cleaned review and a stemmed review are: 

<img src="https://github.com/nhatthangle/Project-Deep-Learning---Text-classification/blob/main/Cleaned%26Stemmed.png" width="1000" height="300" />



## Classification Models

### Part I: Well-known ML classifiers
<p align="justify">
The first part is to try all well-known ML classifiers: 
  
•	Ensemble methods: Bagging of trees, Random Forest, Gradient Boosting, Extreme Gradient Boosting, AdaBoost, LightGBM  \
•	Support Vector Machines methods: Linear SVC and Nonlinear SVM with polynomial and Gaussian kernels \
•	Discriminant Analysis: Linear and Quadratic
</p>

#### Strategy:

We try to perform parameters tuning to enhance the performance of some of these methods, the rest takes too long to tune.
 

### Part II: Neural network models

<p align="justify">
The second part will focus on Neural Network models:
  
•	Basic Sequential models \
•	RNN models: LSTM models \
•	CNN model
  
The main focus is to try enhance model performance by adapting different optimization algorithms such as SGD (mini-batch, batch), RMSProp, Adam etc. and by imposing regularization methods such as l1, l2 regularizations, dropout, batch-normalization, early stopping, weight initilizations and combinations of them.
</p>

As has been said above, we will perform classification on both cleaned data without stemming and the stemmed data.

### Strategy:

First, we try the usual Sequential models with different optimization methods: SGD, mini-batch SGD, batch SGD, RMSProp, Adam on the crude Sequentila models to see which method is opitmal. Next, we use the optimal methods (according to the results) RMSProp and Adam as default for the models that follows and add combinations of regularization methods l1, l2, batch normalization, dropout to see if they work. After this, we implement other regularization methods such as Xavier weight initializations and early stopping.

Second, we implement an RNN model, namely LSTM model (stands for Long Short Term Memory) with optimization methods Adam and RMSProp and play with the regularization methods again. We also add try fastText embedding on these models.

Third, we build a simple CNN model, which is uasually used for image classification. However, in this case, we can still implement it for text classification using some modification. 

## Results 

### First part: Well-known machine learning classifiers and hyperparameters tuning

#### Before tuning

We would like to present the results of the first part using well-know machine learning algorithms. We used 4 different metrics to evaluate how good the performance is: accuray, weighted f1, weighted precision and weighted recall. The main focus is still the accuracy rate. Below is the table of metrics for cleaned data and stemmed data. The algorithms used in this were not tuned.
  
<img src="https://github.com/nhatthangle/Project-Deep-Learning---Text-classification/blob/main/ML.png" />

<p align="justify">
  
In the picture above, the left table is for cleaned data without stemming and the right table is for stemmed data. As can be see, stemming makes it worse in each classifier. Nonlinear SVC - Gaussian Kernel wins in the cleaned data and LinearSVC wins in the stemmed data but NSVC- Gaussian Kernel is just slightly lower than Linear SVC

</p>

#### After tuning

### Second part: Neural network models

#### Sequential models 


#### LSTM models

#### CNN model



