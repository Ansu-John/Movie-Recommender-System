# Movie Recommender System

### OBJECTIVE
Recommender systems are information filtering tools that aspire to predict the rating for users and items, predominantly from big data to recommend their likes. Movie recommendation systems provide a mechanism to assist users in classifying users with similar interests. This makes recommender systems essentially a central part of websites and e-commerce applications.

### DATASET USED
Data taken from [Grouplens site](https://grouplens.org/datasets/movielens/1m/) and contain 1 million ratings from 6000 users on 4000 movies. 

### TOOLS
Spark and Python - PySpark, ALS, RegressionEvaluator

### TECHNIQUES
I have used Apache Spark ML, alternating least squares (ALS) for collaborative filtering for making recommendations. Alternating least square(ALS) matrix factorization basically take a large (or potentially huge) matrix and factor it into some smaller representation of the original matrix through alternating least squares. We end up with two or more lower dimensional matrices whose product equals the original one. ALS comes inbuilt in Apache Spark.

#### Approaches to Recommendations
There are two widely used approaches for building recommender system. They are the content-based filtering (CBF) and collaborative filtering (CF).![Image](https://github.com/Ansu-John/Movie-Recommender-System/blob/main/Recommender%20System.jpg) 

##### Content-based Filtering (CBF): 
The main idea behind CBF is to recommend items similar to the items previously liked by the user. For example, if the user have rated some items in the past, then these items are used for user-modeling where the user’s interests are quantified.

This can be achieved in two different ways:
- Predicting ratings using parametric models like regression or logistic regression for multiple ratings and binary ratings respectively based on the previous ratings.
- Similarity based techniques using distance measures to find similar items to the items liked by the user based on item features.

CB can be applied even when a strong user-base is not built, as it depends on the item’s meta data (features) therefore does not suffer from cold-start problem. However, this also makes it computationally intensive, as similarities between each user and all the items must be computed. Since the recommendations are based on the item similarity to the item that the user already knows about, it leaves no room for serendipity and causes over specialisation. CB also ignores popularity of an item and other users feedbacks.

##### Collaborative filtering (CF) :
Collaborative filtering aggregates the past behaviour of all users. It recommends items to a user based on the items liked by another set of users whose likes (and dislikes) are similar to the user under consideration. This approach is also called the user-user based CF. Item-item based CF became popular later, where to recommend an item to a user, the similarity between items liked by the user and other items are calculated. 

The user-user CF and item-item CF can be achieved by two different ways, memory-based (neighbourhood approach) and model-based (latent factor model approach).
- The memory-based approach : 
Neighbourhood approaches are most effective at detecting very localized relationships (neighbours), ignoring other users.
- The model-based approach : 
Latent factor model based collaborative filtering learns the (latent) user and item profiles (both of dimension K) through matrix factorization by minimizing the RMSE (Root Mean Square Error) between the available ratings y and their predicted values yˆ.
