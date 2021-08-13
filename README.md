# RecommendationSystemProject
1. [Project Introduction](#motivation)
2. [Project Summary and Thoughts](#summary)
4. [Licensing, Authors, and Acknowledgements](#licensing)


 
## 1. Project Introduction<a name="motivation"></a>
It this project, it analyzes the interactions that users have with articles on the IBM Watson Studio platform, and makes recommendations on new articles they will like. The project are divided into the following tasks

I. Exploratory Data Analysis

Before making recommendations of any kind, explore the data in the project. 

II. Rank Based Recommendations

To get started in building recommendations, first find the most popular articles simply based on the most interactions. Since there are no ratings for any of the articles, it is easy to assume the articles with the most interactions are the most popular. These are then the articles we might recommend to new users (or anyone depending on what we know about them).

III. User-User Based Collaborative Filtering

In order to build better recommendations for the users of IBM's platform, we could look at users that are similar in terms of the items they have interacted with. These items could then be recommended to the similar users. This would be a step in the right direction towards more personal recommendations for the users. You will implement this next.

IV. Content Based Recommendations (EXTRA - NOT REQUIRED-DONE)

Given the amount of content available for each article, there are a number of different ways in which someone might choose to implement a content based recommendations system. NLP is used to develop a content based recommendation system here. 

V. Matrix Factorization

Finally, you will complete a machine learning approach to building recommendations. Using the user-item interactions, you will build out a matrix decomposition. Using your decomposition, you will get an idea of how well you can predict new articles an individual might interact with (spoiler alert - it isn't great). You will finally discuss which methods you might use moving forward, and how you might test how well your recommendations are working for engaging users.

## 2. Project Summary and Thoughts<a name="summary"></a>
I. Content Based Recommendations(EXTRA)

- Pathway

Content features, essentially key words was identified by condcting NPL analysis on article titles. Dot product was used to calculate the similarities among articles based on article features. Given a certain article, the most similar articles is provided based on dot product result.

- Code

While conducting NPL analysis, pipeline was used to keep the process clean and easy to alter later on.

- A comprehensive recommendation solution blending with content-based recommendation, collaborative filtering and knowledge based solutions.
The recommendation system has been further built into a comprehensive one: blend with content-based recommendation, collaborative filtering and knowledge based solutions. It expands the capability to give recomendations to either articles or users in database, and even to brand new users.

II. Matrix Factorization Solution 

- Cold Start Problem 

Regarding the current Matrix Factorization Solution, it couldn't handle cold start probelem. In other words, it couldn't provide recommendations for users that are not in the training set. In such case, content based and ranked based solutions are way to go for new users.

- Evaluation metrics
Accuracy was used to evaluate the model's performance. One issue was that while calculating the accuracy, the sum of absolute error was divided by the size of user_by_article matrix. Considering that the user_by_article matrix was very sparsed, and huge amount of user-article had none connections. The accuracy wasn't calculated correctly. Instead, we should only count the number of user-article that had connections, and evaluate the prediction errors upon those. Specifically, the sum of absolute error should be divided by the number of non-0 user-article counts.

- Metrics selection
Regarding metrics selection for model evaluation, accuracy was used in this case. However,accuracy metric is mostly for classification model evalution. To make a fair asscessment of the model, regression metrics are more appropriate, for exaple,vMean-Squared Error (MSE). 

- Evaluation robustness  issue
The dataset was splited into training and testing sets. But it only got 20 users in testing set that could be used for model validation, as such users were also in the training set. The very limited number of users for model validation was not sufficient and not robust for evaluating the model. We could futher shuffle datasets before spliting training/testing data sets and iterate modeling process for stable and more convincing evaluation results.

- Offline/Online recommendation issue
The recommendation in this practice actually don't work very well for offline testing. In offline testing, it is ideal to not just obtain a list of recommendations for each individual, because we ultimately don't know if a user doesn't read an article because they don't like it, or because they just haven't read it yet (but would like it). Rather, it would be great if we have an idea of how much each user would like each item using a predicted rating. Then we can compare this predicted rating to the actual rating any individual gives to an item in the future.

Moreover,  an online evaluation technique like A/B testing can be further used. It is common in practice to set up online recommendations to have an "old" version of recommended articles, which is compared to a new system that uses the new recommendation strategy. In practice, metrics like higher engagement, clicks can be used to evaluate A/B testing result.

## 3. Licensing, Authors and Acknowledgements<a name="licensing"></a>
Must give credit to IBM for the data.

Thanks to Udacity community's knowledge sharing that supports the project.
