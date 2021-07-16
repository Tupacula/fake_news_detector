# fake_news_detector

My goal is to create a model to predict whether an article is "fake" or "real"

# EDA

![mostfakewords](https://user-images.githubusercontent.com/57776494/126005503-6a512459-b1ab-415d-a3f4-6154795db947.png)
![mosttruewords](https://user-images.githubusercontent.com/57776494/126005510-8d81ea48-fa28-434f-98a9-fce60c37905e.png)
 Here are the most common words in fake and real, as you can see some feature engineering will be required since I don't want the model to use keys like (reuters) to inform prediction
 
 # Feature Engineering
 
 I removed any reference to the organization that the article originated from
 
 I removed non american articles
 
 used a TFIDF Vectorizer for a pipeline with ngrams allowed to range from 1 to 2
 
 ![new_subjects](https://user-images.githubusercontent.com/57776494/126012002-fb5eec1e-ff85-4dca-94d7-7f213c4e09ad.png)
![truevsfake](https://user-images.githubusercontent.com/57776494/126012009-ba00acbf-e3d0-4c5a-af0f-6beea5cd8ca7.png)
![truevsfakenew](https://user-images.githubusercontent.com/57776494/126012016-30ca5923-9382-424a-9f82-7c4d64c7aa2c.png)
Proportion of Real to Fake goes from roughly 50/50 to 66/33 in favor of Fake articles

# Best Model

![Screenshot from 2021-07-16 14-38-38](https://user-images.githubusercontent.com/57776494/126012116-2926a613-f98f-40d3-b634-45f43f2edf19.png)
![naivebayescm](https://user-images.githubusercontent.com/57776494/126012124-de5f18f8-d2a4-4ec0-8d58-247c30622ae8.png)

Gradient Boosting is the best model

#Feature Importance

top 20 most important words

![Screenshot from 2021-07-16 16-16-25](https://user-images.githubusercontent.com/57776494/126013883-5ce63d09-5793-497e-92eb-7cfff0d02433.png)
