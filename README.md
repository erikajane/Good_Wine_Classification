# Good or Bad Wine Classification

## Introduction

When looking for a new wine to try, the hope is that you pick a good one. Unfortuantely, you won't know that wine is good or not until you taste it. Luckily if you are able to obtain the physiochemical properties of the wine you intend on buying, you can figure out if the wine is good or not.

What makes a 'high quality' wine, 'high quality'? (What features does a high quality wine include?

Can we predict whether a wine is 'high quality' or not by looking at it's features?

## The Data

From University of California, Irvine’s Machine Learning Repository, two datasets were utilized, __winequality-red__ and __winequality-white__ (https://archive.ics.uci.edu/ml/datasets/wine+quality). The two datasets include physicochemical information  on either red or white wine samples from Northern Portugal. The following twelve physicochemical features for each observed wine sample are as follows:

 - fixed acidity
 - volatile acidity
 - citric acid
 - residual sugar
 - chlorides
 - free sulfur dioxide
 - total sulfur dioxide
 - density
 - pH
 - sulphates
 - alcohol
 - quality

Since the goal of this project is to determine whether a wine is good or bad, we will be trying to predict quality (scored between 1 and 10), using the other features included in the dataset.

## Data Preprocessing and Exploratory Data Analysis

### Red Wine

The red wine dataset included 1599 observations, but after dropping 240 duplicates, 1359 observations remain.

Although, quality is scored on a scale of 1 through 10, we see that the red wine samples only scored quality scores between 3 and 8. The majority of wine had been given scores of 5 and 6.

##### Insert Picture Here (Red_Wine_Quality_Distribution.png)

Since the goal is to classify whether a wine is good or bad, the quality scores are reassigned. Wines  with a quality of 6 and below are assigned a numberic value of __0__ and will be considered _'bad wines'_ and wines with a quality score of 7 and above are reassigned a value of __1__ and will be considered _'good wines'_.

##### Insert Picture Here (Red_Wine_Good_Bad_Distribution.png)

After binning our target variable, quality, into binary variables for good and bad wine, the dataset now has __1,175 Bad Wines__ and __184 Good Wines__.

##### Insert Picture Here (Red_Wine_Good_Bad_Wine_Distribution_Stats.png)

#### Fixed Acidity, Volatile Acidity and Citric Acid

##### Insert Picture Here (Acid_vs_Quality.png)

 - _Good Wines_ on avergage, tend to have slightly __higher Fixed Acidity__ levels than _Bad Wines_
 - _Good Wines_ on avergage, tend to have __lower Volatile Acidity__ levels than _Bad Wines_
 - _Good Wines_ on avergage, tend to have __higher Citric Acid__ levels than _Bad Wines_

#### Sulphates, Free Sulfur Dioxide and Total Sulfur Dioxide

##### Insert Picture Here (Sulfur_vs_Quality.png)

 - _Good Wines_ on avergage, tend to have slightly __higher Sulphates__ levels than _Bad Wines_
 - _Good Wines_ on avergage, tend to have __lower Free Sulfur Dioxide__ levels than _Bad Wines_
 - _Good Wines_ on avergage, tend to have __lower Total Sulfur Dioxide__ levels than _Bad Wines_
 
 #### Alcohol, Denisty and pH
 
 ##### Insert Picture Here (Other_Features_vs_ Quality.png)

 - _Good Wines_ on avergage, tend to have __higher Alcohol__ levels than _Bad Wines_
 - _Good Wines_ on avergage, tend to have __the same Density__ levels as _Bad Wines_
 - _Good Wines_ on avergage, tend to have __theh same pH__ levels as _Bad Wines_
 
 #### Feature Correlation with Quality
 
 ##### Insert Picture Here (RW_Feature_Correlation_with_Quality.png)
 
 The features with the strongest correlation to Quality are as follows:
 
 - alcohol (0.409926)
 - volatile acidity (-0.267344)
 - citric acid (0.203561)
 - sulphates (0.201551)
 - density (-0.158052)
 
 ### White Wine
 
 ## Modeling 
 
 ### Red Wine
 
 #### Handle Class Imbalance
 
 Before we start modeling, the class imbalance within the dataset needs to be addressed. There are significantly more _Bad Wine_ observations than there are _Good Wine_ observations. After spliting the data, using 25% of the data for testing, the distribution of the trainng dataset is 135 _Good Wines_ and 884 _Bad Wines_. After upsampling the _Good Wines_, the number of _Good Wines_ in the training dataset is 263 and there are still 884 _Bad Wines.  

  
  
 
 