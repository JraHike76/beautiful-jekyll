---
layout: post
title: "I'd sleep there"
subtitle: "Take a trip back to 2016 and visit Seattle... Air BnB reviews"
tags: [Data Science, Data Science Student, Machine Learning, Air BnB, Seattle]
---
<p align="center">
  <img width="300" height="200" src="https://i.imgur.com/aMYAXoi.png?1" class="align-center">
</p>


# **Introduction**
As I stumbled upon this dataset that was scraped in January of 2016, I felt it deserved further analysis. After looking over the data held within it's 92 columns and close to 4000 observations I wanted to see how well I could recommend these rental properties based on the various reviews. 

# **My Process**
While first analyzing the data I found many columns to be unuseful such as URL's and categories with only one unique identifier. For instance in the column 'state' Washington is included in every observation. Luckily for me the original creator of this dataset who web-scraped the data from Air BnB' website created a feature based on several review categories such as  Student also explains: Why & how they chose their target, metric, and baseline. How they avoided leakage. When & why the model is (or is not) useful

**Looking and the balance of classes for the target highly_recommend**
<p align="center">
  <img width="450" height="275" src="https://i.imgur.com/NZuv8Bf.png" class="align-center">
</p>


# **Interactive Map: all properties in the data**
{% include figure.html %}









<p align="center">
  <img width="250" height="250" src="https://i.imgur.com/n4NVO3e.png" class="align-center">
</p>
