# python_kaggle_flipkart_sentiment_analysis
Runs on the dataset in Kaggle at https://www.kaggle.com/datasets/niraliivaghani/flipkart-product-customer-reviews-dataset

Neural Network Categorical Classification, cardinality 3¶
This copy updates the 205000+ rows and has the ability to write it out as a CSV (uncomment and run the last code block). This performs a sentiment analysis, trained on the original sentiments using Rate, Review and Price as predictor features. A new column NN-sentiment is added and results are reported here:

There were a total of 46161 changes in sentiment Accuracy against the full training set is 0.7748814934748259

Total changed from positive to neutral 0 Total changed from positive to negative 16941 Total changed from neutral to positive 8467 Total changed from neutral to negative 1732 Total changed from negative to neutral 0 Total changed from negative to positive 19021

I'm not saying this is better or worse (probably worse) than the original sentiments. What I'm suggesting is if some were to be double checked against other ways of examining the sentiment the results here suggest about 22% fall into the re-examination category.

This Notebook takes about 50 to 60 minutes to execute on the Kaggle servers. It reports: 1282/1282 [==============================] - 2s 2ms/step - loss: 0.2881 - accuracy: 0.9170 Test accuracy: 0.9170466661453247 Test loss: 0.2881276607513428

Many thanks also to NIRALII VAGHANI AND 1 COLLABORATOR · UPDATED A MONTH AGO for the data. It follows the design pattern in the Intro To Deep Learning tutorial here at Kaggle. If you read through this, and the Tutorial, you'll find this is highly parallel in how the pipeline is built and used in the Tutorial on binary classification. I watched one of Rob Mulla's videos related to this type of network a while back and got the basics for how to solve the classification problem for negative, neutral, and positive sentiment (flatten and then bring the connections together for each dummy created for the categorical output). I asked ChatGPT/Bing for advice with Pandas and type conversion. Both gave about the same answer.

Here is how it works:

Lots of data cleansing, NaN and cannot convert string to float took most of the time to clean out.
It uses three features: product_price, Review, and Rate.
Rate is treated as a categorical feature and put through OneHot in the pipeline.
product_price is just a float and stays that way.
Review occurs 1324 times uniquely (most people say something similar to many others when just writing a few words).
5.1. The Python singleton class CatVarStorageLabels is used to keep a map of Review occurrences and a unique integer is assigned to each unique occurrence for use in the input vector (tensor). 
5.2. The data from CatVarStorageLabels is written to a file. If a productized predictor were used the model would also need to be written to a file and loaded for use when required. Vectorization from CatVarStorageLabels's data would need to be added to the productized version. Use 0.0 if not found (0.0 was not included and thus should not contribute).

Yes, odds are using a sentiment detector on the Summary and Reviews, is probably better or added to this. With over 200,000 samples however, I felt this was a good data set for training a network.
