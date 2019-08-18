# Is This Wine Good?

## Introduction

When looking for a new wine to try, the hope is that you pick a good one. Unfortunately, you won't know that wine is good or not until you taste it. Luckily if you are able to obtain the physiochemical properties of the wine you intend on buying, you may be able to figure out if the wine is good or not.

The goal of this project was to determine if a _good wine_ could be predicted from its physiochemical properties.

## The Data

From University of California, Irvine’s Machine Learning Repository, the dataset, __winequality-red__ was utilized (https://archive.ics.uci.edu/ml/datasets/wine+quality). The dataset included physicochemical information on red wine samples from Northern Portugal. The following twelve physicochemical features for each observed wine sample are as follows:

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

Since the goal of this project was to determine whether a wine was good or bad, I tried to predict quality (scored between 1 and 10), using the other features included in the dataset.

## Data Preprocessing and Exploratory Data Analysis

The red wine dataset included 1,599 observations, but after dropping 240 duplicates, 1,359 observations remained.

Although, quality was scored on a scale of 1 through 10, the red wine samples only received quality scores between 3 and 8. The majority of wine had been given quality scores of 5 and 6.

![Red_Wine_Quality_Distribution.png](https://github.com/erikajane/Good_Wine_Classification/blob/master/Images/Red_Wine_Quality_Distribution.png)

Since the goal was to classify a wine as good or bad, the target variable, quality, was turned into a binary feature. Wines with a quality of 6 and below were assigned a numeric value of __0__ and were considered _'bad wines'_ and wines with a quality score of 7 and above were reassigned a value of __1__ and were considered _'good wines'_.

![Red_Wine_Good_Bad_Distribution.png](https://github.com/erikajane/Good_Wine_Classification/blob/master/Images/Red_Wine_Good_Bad_Distribution.png)

After binning the target variable, the dataset included __1,175 Bad Wines__ and __184 Good Wines__.

![Red_Wine_Good_Bad_Wine_Distribution_Stats.png)](https://github.com/erikajane/Good_Wine_Classification/blob/master/Images/Red_Wine_Good_Bad_Wine_Distribution_Stats.png)

### Fixed Acidity, Volatile Acidity and Citric Acid

![RW_Acid_vs_Quality.png)](https://github.com/erikajane/Good_Wine_Classification/blob/master/Images/RW_Acid_vs_Quality.png)

 - _Good Wines_ on average, tended to have slightly __higher Fixed Acidity__ levels than _Bad Wines_
 - _Good Wines_ on average, tended to have __lower Volatile Acidity__ levels than _Bad Wines_
 - _Good Wines_ on average, tended to have __higher Citric Acid__ levels than _Bad Wines_

### Sulphates, Free Sulfur Dioxide and Total Sulfur Dioxide

![RW_Sulfur_vs_Quality.png)](https://github.com/erikajane/Good_Wine_Classification/blob/master/Images/RW_Sulfur_vs_Quality.png)

 - _Good Wines_ on average, tended to have slightly __higher Sulphate__ levels than _Bad Wines_
 - _Good Wines_ on average, tended to have __lower Free Sulfur Dioxide__ levels than _Bad Wines_
 - _Good Wines_ on average, tended to have __lower Total Sulfur Dioxide__ levels than _Bad Wines_
 
### Alcohol, Denisty and pH
 
![RW_Other_Features_vs_ Quality.png](https://github.com/erikajane/Good_Wine_Classification/blob/master/Images/RW_Other_Features_vs_%20Quality.png)

 - _Good Wines_ on average, tended to have __higher Alcohol__ levels than _Bad Wines_
 - _Good Wines_ on average, tended to have __the same Density__ levels as _Bad Wines_
 - _Good Wines_ on average, tended to have __the same pH__ levels as _Bad Wines_
 
### Feature Correlation with Quality

![RW_Feature_Correlation_with_Quality.png](https://github.com/erikajane/Good_Wine_Classification/blob/master/Images/RW_Feature_Correlation_with_Quality.png)
 
 The features with the strongest correlation to Quality are as follows:
 
 - alcohol (0.409926)
 - volatile acidity (-0.267344)
 - citric acid (0.203561)
 - sulphates (0.201551)
 - density (-0.158052)
 
## Modeling & Results

In a situation where you are either looking to sell _good wine_ or drink _good wine_, you will want to reduce the number of false positives (predicting a wine is good when it is not) as much as possible. If you sell someone a bottle of wine and you tell them it is good, they will be extremely disappointed that it is not good when they taste it. Not only is this embarrassing for a restaurant or store owner but this situation could hurt their business and lead to them losing customers. The situation is similar for a buyer of wine, if they had gone out of their way to buy a ‘good’ bottle of wine, they will not be happy when they find that it is not a _good quality wine_. This is why false positives are bad in this situation. We are not nearly as concerned with false negatives here. If someone buys or sells a bottle of wine that is predicted to be a _bad quality wine_ and it turns out to be a _good quality wine_, they will end up being happily surprised that the wine is better than intended and no harm done to the wine buyer or wine seller. In an effort to ensure the false positive count was not too great, __precision was optimized__ when modeling.

Five models were employed; __Logistic Regression, Decision Tree, Random Forest, XG Boost and SVM__. Each model was run twice, once with the original features and once with the the original features converted into polynomial combinations using __PolynomialFeatures__ from __scikit-learn__.

### Handle Class Imbalance
 
Before modeling, the class imbalance within the dataset needed to be addressed. There were significantly more _bad wine_ observations than there were _good wine_ observations. After splitting the data, using 75% of the data for training, the distribution of the training dataset was 135 _good wines_ and 884 _bad wines_. After upsampling the _good wines_ by 195% of its original value, the number of _good wines_ in the training dataset became 263 while the _bad wine_ count reamained 884. Although there was still class imbalance, it was better than what it was before and helped prevent the models over-predicting _bad wines_.

### Best Model

The best model for predicting _good red wines_ was the __SVM model using the original features__, with a __precision of 81.81%__ and an __accuracy of 89.7%__. When looking at the confusion matrix below we do see that the model over-predicted the _bad wines_ but that was to be expected with a target variable as imbalanced as the one used here. With this model, one can buy a _good wine_ and be happy with their purchase 81.81% of the time, however this model will limit the number of _good wines_ it recommends.

![Confusion_Matrix.png](https://github.com/erikajane/Good_Wine_Classification/blob/master/Images/Confusion_Matrix.png)

  
 
 