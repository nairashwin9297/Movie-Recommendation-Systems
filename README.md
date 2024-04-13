# Movie-Recommendation-System

![netflix_movies_cover](https://user-images.githubusercontent.com/69259443/117538449-dd6a3080-b023-11eb-8b02-1d4ecea87f8b.jpg)

---

## Demo
![image1](https://user-images.githubusercontent.com/69259443/117534444-1ba92500-b00f-11eb-8068-5b4bcf9e883c.png)
![image2](https://user-images.githubusercontent.com/69259443/117534455-2b286e00-b00f-11eb-8e57-0aeb90f4b15d.png)
![image3](https://user-images.githubusercontent.com/69259443/117534462-34b1d600-b00f-11eb-8f93-1f7fe25d879e.png)

---

## Overview

#### [Reference](https://www.analyticsvidhya.com/blog/2020/11/create-your-own-movie-movie-recommendation-system/)

**Recommendation System** is a filtration program whose prime goal is to predict the “rating” or “preference” of a user towards a domain-specific item or item. In our case, this domain-specific item is a movie, therefore the main focus of our recommendation system is to filter and predict only those movies which a user would prefer given some data about the user him or herself.\
What are the different filtration strategies?
![image4](https://user-images.githubusercontent.com/69259443/117534761-71320180-b010-11eb-847f-4c859b255a9f.png)

---

**1) Content-based Filtering**\
This filtration strategy is based on the data provided about the items. The algorithm recommends products that are similar to the ones that a user has liked in the past. This similarity (generally cosine similarity) is computed from the data we have about the items as well as the user’s past preferences.
For example, if a user likes movies such as ‘The Prestige’ then we can recommend him the movies of ‘Christian Bale’ or movies with the genre ‘Thriller’ or maybe even movies directed by ‘Christopher Nolan’.So what happens here, the recommendation system checks the past preferences of the user and find the film “The Prestige”, then tries to find similar movies to that using the information available in the database such as the lead actors, the director, genre of the film, production house, etc and based on this information find movies similar to “The Prestige”.

**Disadvantages**
1) Different products do not get much exposure to the user.
2) Businesses cannot be expanded as the user does not try different types of products.
---
**2) Collaborative Filtering**\
This filtration strategy is based on the combination of the user’s behavior and comparing and contrasting that with other users’ behavior in the database. The history of all users plays an important role in this algorithm. The main difference between content-based filtering and collaborative filtering that in the latter, the interaction of all users with the items influences the recommendation algorithm while for content-based filtering only the concerned user’s data is taken into account.\
There are multiple ways to implement collaborative filtering but the main concept to be grasped is that in collaborative filtering multiple user’s data influences the outcome of the recommendation. and doesn’t depend on only one user’s data for modeling.

There are 2 types of collaborative filtering algorithms:

   * **User-based Collaborative filtering**\
       The basic idea here is to find users that have similar past preference patterns as the user ‘A’ has had and then recommending him or her items liked by those          similar users which ‘A’ has not encountered yet. This is achieved by making a matrix of items each user has rated/viewed/liked/clicked depending upon the task        at hand, and then computing the similarity score between the users and finally recommending items that the concerned user isn’t aware of but users similar to          him/her are and liked it.\
       For example, if the user ‘A’ likes ‘Batman Begins’, ‘Justice League’ and ‘The Avengers’ while the user ‘B’ likes ‘Batman Begins’, ‘Justice League’ and ‘Thor’          then they have similar interests because we know that these movies belong to the super-hero genre. So, there is a high probability that the user ‘A’ would like        ‘Thor’ and the user ‘B’ would like The Avengers’.

       **Disadvantages**\
         a) People are fickle-minded i.e their taste change from time to time and as this algorithm is based on user similarity it may pick up initial similarity                 patterns between 2 users who after a while may have completely different preferences.\
         b) There are many more users than items therefore it becomes very difficult to maintain such large matrices and therefore needs to be recomputed very      regularly.\
         c) This algorithm is very susceptible to shilling attacks where fake users profiles consisting of biased preference patterns are used to manipulate key   decisions.

   * **Item-based Collaborative Filtering**\
       The concept in this case is to find similar movies instead of similar users and then recommending similar movies to that ‘A’ has had in his/her past                  preferences. This is executed by finding every pair of items that were rated/viewed/liked/clicked by the same user, then measuring the similarity of those            rated/viewed/liked/clicked across all user who rated/viewed/liked/clicked both, and finally recommending them based on similarity scores.\
       Here, for example, we take 2 movies ‘A’ and ‘B’ and check their ratings by all users who have rated both the movies and based on the similarity of these              ratings, and based on this rating similarity by users who have rated both we find similar movies. So if most common users have rated ‘A’ and ‘B’ both similarly        and it is highly probable that ‘A’ and ‘B’ are similar, therefore if someone has watched and liked ‘A’ they should be recommended ‘B’ and vice versa.

       **Advantages over User-based Collaborative Filtering**\
         a)Unlike people’s taste, movies don’t change.\
         b)There are usually a lot fewer items than people, therefore easier to maintain and compute the matrices.\
         c)Shilling attacks are much harder because items cannot be faked.

**This project aims to find top 20 similar movies the user is expected to watch given his current movie choice. The project takes into account both content and collaborative base filtering and creates an option for hybrid filtering which is the average of both.** 

---

## Motivation 
Being someone who used spend a lot of time on social media, I often wondered how these platforms kept their audience hooked onto them. After learning that there are smart machine learning algorithms which predict the user behavior, I ended up reading more about movie recommendation systems and wanted to build one myself. While the UI/UX part of it is still under development, I was able to build the basic running model of the recommender.

---

## Technical Aspects

* **Cosine similarity**\
Cosine similarity is a metric used to measure how similar the two items or documents are irrespective of their size. It measures the cosine of an angle between two vectors projected in multi-dimensional space. This allows us to measure the similarity of a document of any type. Due to a multi-dimensional array, any number of variables (which are treated as dimensions) can be used, which in turn supports large sized documents.

Mathematically, the cosine of the angle of between two vectors is derived from the dot product of the two vectors divided by the product of the two vectors’ magnitude.

![image5](https://user-images.githubusercontent.com/69259443/117536113-e274b300-b016-11eb-9002-3f3c815007a5.png)

Since we are finding the cosine of two vectors the output will always range from -1 to 1, where -1 shows that two items are dissimilar and 1 shows that two items are completely similar.

* **SVD**\
SVD (Singular Value Decomposition) in NLP can be used for text mining. When you have a matrix of documents/words, SVD can reduce the dimension of your matrix. In NLP , it is used to study the relation between documents and words.
This transformer performs linear dimensionality reduction by means of truncated singular value decomposition (SVD). It is very similar to PCA, but operates on sample vectors directly, instead of on a covariance matrix. This means it can work with scipy.sparse matrices efficiently.
In particular, truncated SVD works on term count/tf-idf matrices as returned by the vectorizers in sklearn.feature_extraction.text.
 
