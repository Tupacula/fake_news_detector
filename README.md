# fake_news_detector

My goal is to create a model to predict whether an article is "fake" or "real"

# Description of Data

I downloaded the dataset from the university of victoria: https://www.uvic.ca/engineering/ece/isot/datasets/fake-news/index.php


"The dataset contains two types of articles fake and real News. This dataset was collected from realworld sources; the truthful articles were obtained by crawling articles from Reuters.com. As for the fake news articles, they were collected from different sources. The fake news
articles were collected from unreliable websites that were flagged by Politifact and Wikipedia. The dataset contains different types of articles on different topics, however, the majority of articles focus on political and World news topics.

The dataset consists of two CSV files. The first file named “True.csv” contains more than 12,600
articles from reuter.com. The second file named “Fake.csv” contains more than 12,600 articles from
different fake news outlet resources. Each article contains the following information: article title, text,
type and the date the article was published on. All articles are originate between the years of 2015 and 2017.

# EDA




![mostfakewords](https://user-images.githubusercontent.com/57776494/126005503-6a512459-b1ab-415d-a3f4-6154795db947.png)
![mosttruewords](https://user-images.githubusercontent.com/57776494/126005510-8d81ea48-fa28-434f-98a9-fce60c37905e.png)
 Here are the most common words in fake and real, as you can see some feature engineering will be required since I don't want the model to use keys like (reuters) to inform prediction
 
 # Feature Engineering
 
 I removed any reference to the organization that the article originated from
 
 I removed non american articles because the dataset was very unbalanced (nearly half of the true articles are realted to world news, whereas only a few hundred fake news articles are). Otherwise my model would pick out words like "Paris" or "England" as important features.
 
 
 Then I used a TFIDF Vectorizer for a pipeline with ngrams allowed to range from 1 to 2
 
 ![new_subjects](https://user-images.githubusercontent.com/57776494/126012002-fb5eec1e-ff85-4dca-94d7-7f213c4e09ad.png)
![truevsfake](https://user-images.githubusercontent.com/57776494/126012009-ba00acbf-e3d0-4c5a-af0f-6beea5cd8ca7.png)
![truevsfakenew](https://user-images.githubusercontent.com/57776494/126012016-30ca5923-9382-424a-9f82-7c4d64c7aa2c.png)

As you can see the proportion of Real to Fake goes from roughly 50/50 to 66/33 in favor of Fake articles

# Best Model

![Screenshot from 2021-07-16 14-38-38](https://user-images.githubusercontent.com/57776494/126012116-2926a613-f98f-40d3-b634-45f43f2edf19.png)
![naivebayescm](https://user-images.githubusercontent.com/57776494/126012124-de5f18f8-d2a4-4ec0-8d58-247c30622ae8.png)

Gradient Boosting (Confusion Matrix on left) Decision Trees is the best model since it has the highest F1 score of the models tested. For comparison, a confusion matrix constructed from use of Naive Bayes is on the right.

# Feature Importance

Here are the most important words (using gini importance) the model uses for determining what category (fake or true) an article falls into

![Screenshot from 2021-07-16 16-16-25](https://user-images.githubusercontent.com/57776494/126013883-5ce63d09-5793-497e-92eb-7cfff0d02433.png)

# Conclusion/Next Steps

As you can see from the confusion matrix, the model performs very well. So well, in fact, that I wonder if there is some leakage in the data, or my model is picking up on the fact that true articles and false articles come from a particular set of news agencies with no overlap. This warrants further investigation. 

I would also want to use more state of the art models such as Bert - a pretrained neural network that tries to model connections between words (since, intuitively, the presence of one word is a predictor for the presence of another in a given article, and that relationship isn't really captures by any of the models tested, which really just looks at the overall presence of any group of words) in the hopes of improving my predictions.
