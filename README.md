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

![image](https://user-images.githubusercontent.com/22790699/179383856-ac7479ed-debc-45eb-ba99-3c15b77ed2fd.png)
![image](https://user-images.githubusercontent.com/22790699/179383868-c7ef51c6-9c5c-435b-afbc-5b8a8584b8f3.png)


## Preprocessing:

* Removing dump articles - Articles with no words 

* Removing columns which don’t have relationship with Number of shares – Like URL of article, Timedelta – Not a feature

* Removing highly correlated attributes: Unique Stop word with Unique Tokens Stop Words, Average Negative Polarity with Average Positive Polarity, Weekend flag as we already have all weekday 

* Exploring relationship within features – With Correlation plot, Scatter plot 

![image](https://user-images.githubusercontent.com/22790699/179383907-cde7f509-5e7c-4ef6-be1e-e3255b52fa72.png)
![image](https://user-images.githubusercontent.com/22790699/179383898-5cb63eba-8c94-4891-b797-b7c639896885.png)

* We have 51 features as our final predictor variables.


## Unsupervised Learning | Principal Component Analysis

* PCA is a unsupervised method by which the dimensions/ features of the dataset can be reduced. PCA creates news variables that are linear combinations of the original variables. 

* In this particular dataset, usage of PCA would not not be ideal, as the number of components which require to explain the variance is still high.

* After using PCA our model interpretability would be lost. Hence we are not using PCA in our dataset.

![image](https://user-images.githubusercontent.com/22790699/179383942-886f6e87-1973-4801-ade0-29c53dd0c173.png)


## Machine Learning Models and Evaluation | Naïve Bayes, Logistic Regression, KNN, Random Forest

* Random forest model gave the highest accuracy and Area Under Curve(AUC). After hyper-paramter tuning.

![image](https://user-images.githubusercontent.com/22790699/179383959-80833514-d299-4517-9594-d0bd190e998b.png)


## Evaluation of model based on context of problem | Cost Matrix:

*Identifying popular articles correctly will help in increasing the cost at which Advertisements are sold(True Positive)

* While identifying unpopular articles will decrease the ad cost, it will increase number of Advertisement sold although at lower cost (True Negative)

* Loss will be incurred when a Popular article will be predicted as Unpopular, as ads will be sold at lower cost (False Negative)

* Loss will be incurred when an Unpopular article will be predicted as Popular, as ads will be sold at higher cost but eventually, we might lose potential future ads (False Positive)

![image](https://user-images.githubusercontent.com/22790699/179383977-3e728c94-5bdf-43c3-a0e9-fb76f11be721.png)

* Profitability by cost matrix, Random Forest has the highest profitability

* Profitability in no model scenario, with flat rate of $400 for all articles irrespective of popularity

![image](https://user-images.githubusercontent.com/22790699/179383989-769e9b2c-6db2-4061-8e41-7fa1d8d05e62.png)

* The red line indicates - No Model Scenario

* Naive bayes cost performance gives negative lift, based on the cost matrix 

* Form the 4 supervised learning models, random forest has the best profitability. (6.47 mil from 3 mil)

![image](https://user-images.githubusercontent.com/22790699/179383997-39022a4f-2b30-436a-ab99-d060517d1715.png)
