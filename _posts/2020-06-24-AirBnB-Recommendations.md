---
layout: post
title: "I'd sleep there"
subtitle: "Take a trip back to 2016 and visit Seattle... or at least the Air BnB reviews"
tags: [Data Science, Data Science Student, Machine Learning, Air BnB, Seattle]
---
<p align="center">
  <img width="300" height="200" src="https://i.imgur.com/aMYAXoi.png?1" class="align-center">
</p>


### **Introduction**
As I stumbled upon this dataset that was created in January 2016 and graciously posted on Kaggle, I felt it deserved further analysis. After looking over the data held within it's 92 columns and over 3800 observations I wanted to see how well I could recommend rental properties based on the various reviews. The process included a lot of cleaning, creating and converting feature categories, as well as fine-tuning various predictive models. Let's take a look at my journey as I work to recommend Air BnB rental properties. 

### **My Process**
While first analyzing the data I found many columns to be unuseful such as URL's and categories with only one unique identifier. For instance in the column 'state' Washington is included in every observation. I decided that I wanted to use review data to create a target for recommending properties. There were several review categories containing information on various reviews. Luckily for me the original creator of this dataset who web-scraped the data from Air BnB's website created a feature based on several review categories such as the cleanliness of the rebtal and host communication. These reviews were all based on a 1 - 10 scale with 10 being the best. The feature I was most interested in was the average of all reviews in percentage format titled 'review_scores_rating'.

After doing an initial column drop of many categories of URLs and thumbnails, I dropped columns with one unique identifier, and columns of little importance and high variance. It was then time for me to create a target based on 'review_scores_rating' and the percentages contained in that column. I created a new feature titled 'highly_recommend' and set it to anything equal to or higher than 95% then I would highly recommend. All other values, I would not highly recommend. In this process I created a binary classification problem that answers the question "do I highly recommend this rental property?" and the answer is simply yes or no, or in this case true or false.In order to avoid leakage I converted the boolean values to 0s and 1s, with 0 representing no or false, and 1 being yes, I would highly recommend this Air BnB.

At this point I no longer needed 'review_scores_rating' or any of the other review categories, therefore I removed them from the dataframe. I then dropped columns with low impact and high cardinality. After looking at the value counts of the remaining columns I set out to do more feature engineering. I converted all of the remaining categorical columns into classes. For example 'property_type' became House, Apartment or Other, then these strings were converted into numeric values that represented the same information. 

I then had a dataset that I could do some predictive modeling with and hopefully avoid leakage or interaction between the features and target. To identify the property by location I kept latitude and longitude but engineered a low cardinality feature that clustered the coordinates into 5 classes. As another measure of identification, although it contained variance and high cardinality, I kept "property_id' because if I am going to recommend properties, people are going to want to know where they are! 

If you look at the map below you will see that there are no major outliers. Interestingly enough I lived in Seattle during this time and there are clusters of highly recommended locations and locations I would not highly recommend. The blue clusters (class 1) tend to exist in the nicer areas of Seattle where the yellow clusters (class 0) are in less desirable neighborhoods. 

### **Interactive Map: all properties in the data**
{% include figure.html %}

## **Splitting the data and getting a baseline**
Down to only 20 columns I was ready to split the data into a training, validation and test sets. I used a random split where the test data consisted of 20% of the overall data. I then set the X features and y vector for each of these sets of data. Now it was time to creat my baseline. I did this by calculating the value counts of class 1 and 2 in the 'highly_recommend' column of the training data. This returned a baseline of roughly 53% of the rentals that I would highly recommend. 

## **Logistic Regression**
My initial model was linear and I chose logistic regression with ordinal encoding, which gave me an accuracy scor of 65% beating the baseline.  


Student also explains: Why & how they chose their target, metric, and baseline. How they avoided leakage. When & why the model is (or is not) useful


<p align="center">
  <img width="250" height="250" src="https://i.imgur.com/n4NVO3e.png" class="align-center">
</p>
