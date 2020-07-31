
## Book Recommender
This repository contains two essential funtions that a common book recommender system include. The first functionality predicts whether a user will be interested in a particular book given a user-book pair. The second predicts a book's genre given users and text reviews.

#### User-Book Prediction

This part was implemented in the notebook `task1.ipynb`, and was done with a training set (`pairs_Read.txt`) of user-book pairs representing customers' past purchase histories. Every pair (U, B) in the training set shows that the user U has purchased the book B before. Given this piece of information, we were able to make predictions on the test set, which is also a set of user-book pairs. The task was to predict whether the user U will be interested in purchasing book B for pair (U, B). 

The function is then implemented as the following: for every pair (U, B) in the test set, compute the jaccard similarity of users in the training set who have read the book B and the union set of users in the training set who have read either one of the books that the user U has read. The higher the value of jaccard similarity, the more possible the user U will be interested in purchasing the book B. My prediction on test set results in accuracy of 0.81257, ranked in the top 3% during Kaggle competition.

#### Genre Prediction

This part was implemented in the notebook `task2.ipynb`, and was also done with a training set (`pairs_Category.txt`) of user ids, review texts, and reviewed book's genre. With the set of data, we were able to utilize information given by users and texts to make genre predictions. The task was to predict the reviewed book's genre given user id and review text. The genre could be any of Children’s, Comics/Graphic Novels, Fantasy, Mystery/Thriller, and Young Adult.

The function is implemented as the following: User ids are one-hot encoded, and review texts are transformed into lower case, punctuation and stopwords stripped before creating a TF-IDF matrix with tfidfvectorizor. Then, Pipeline and FeatureUnion are used to combine one-hot encoded user ids and tfidf matrix from review text with logistic regression to train data. Although bigram approach was attempted during training, accuracy has rather decreased, and thus I continued with only unigram analysis. Eventually, we obtained a model that could predict a reviewed book's genre given a user and his/her text review. My prediction on test set using the model results in accuracy of 0.74528, ranked in the top 6% during Kaggle competition.
