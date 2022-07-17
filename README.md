# OnlineNewsPopularity
Determining the popularity of online news articles prior to publication, based on weekdays, polarity of the words, and other features.


## Problem:

![image](https://user-images.githubusercontent.com/22790699/179383719-a61b44fb-bb43-4c92-b0d8-229dcbc2b00a.png)


## Data:

The dataset contains:

Rows – 39,000

Features – 61 

Target variable – Number of Shares – This is how popularity is determined by Mashable

Source – UCI Data Repository (https://archive.ics.uci.edu/ml/datasets/online+news+popularity)

Aim – To find articles which will go on to become popular with Machine Learning Models


## Target Variable:

* Shares: Redefining popularity by number of times the article is shared
 
* Number of shares - Continuous

* Conversion of Target Variable to form a Classification problem and defining popularity:

  * Shares>1500 – Popular (1)
  
  * Shares<1500 – Unpopular(0) 

* Why 1500: Balanced dataset – Closer to median

