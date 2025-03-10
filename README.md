# Ames, Iowa Housing Data

<a title="PeryPlanet, Public domain, via Wikimedia Commons" href="https://commons.wikimedia.org/wiki/File:Ames_map.png"><img width="512" alt="Ames map" src="https://upload.wikimedia.org/wikipedia/commons/thumb/2/2c/Ames_map.png/512px-Ames_map.png?20121117200554"></a>

## Table of Contents

1. [Introduction](#introduction)
2. [Data](#data)
3. [Process Outline](#process-outline)
   1. [Initial Observation/Clean](#clean-data)
   2. [Analyze Data](#analyze-data)
   3. [Preprocess Data for Model](#preprocess-data-for-model)
   4. [Model Prediction/Analysis](#model-prediction/analysis)
4. [Next Steps](#next-steps)
5. [References](#references)

## 1 - Introduction <a name="introduction"></a>

A client Pillo Corp. wants to create a model that will help them successfully predict the sale price of a house for their website. They're judging the success of a model based on the RMSE of the log(target) and log(predictions) of the model. They want this number to be 0.13897 or lower to be considered a success.

## 2 - Data <a name="data"></a>
The dataset we're working with is a list of houses from the Ames, Iowa region. Each row in the set is a property with 80 different unique features. Details about features of interest will be discussed in more detail throughout the process outlined below.

## 3 - Process Outline <a name="process-outline"></a>
Process consisted of cleaning, analyzing, and preprocessing for model. Finally, prepared data was run through model for results.

### 3a - Initial Observations/Clean <a name="clean-data"></a>
*[Click here](Notebooks/khp-EDA.ipynb) to jump to the notebook containing Exploratory Data Analysis*

*[Click here](Data-and-Notes/data_description.txt) to jump to the Data Dictionary*

Dataset needed to be cleaned up to fit into machine learning model.

19 of the 80 features had NaNs to be addressed. Six of these -- MasVnrType, MiscFeature, Alley, FireplaceQu, PoolQC and Fence -- had more than 45% missing values. Care needed to be taken before removing info as there are only 1480 rows.

Set consists of sales made between 2006 and 2010. The median sale price is $163,000 with a minimum of $34,900 and a max of $755,000. Each row on the dataset consists of a sale.

### 3b - Analyze Data <a name="analyze-data"></a>
*Sale Price*

Distribution of the sale price, our ultimate target, is skewed right. Will log the target for modeling and predicting and anti-log for presentation.

![SalePrice_dist](https://github.com/user-attachments/assets/6032fbcf-8947-4836-b3b7-095253f432b0)

*Features missing more than 45%*

As previously mentioned, the dataset is small, so extra precaution was taken for columns missing large amounts of data. Looking to avoid dropping items if possible.

1. MasVnrType - a few lines had data missing at random. The remaining were actually houses that had no masonry, so those NaNs were imputed with "NA" per the data dictionary
   
3. MiscFeature, Alley, FireplaceQu, PoolQC, Fence - imputed with "NA" per data dictionary. All these categories simply did not have these particular features (misc, next to alley, fireplace, pool, fence) so they were not missing at random

*Correlation*

Correlation heatmap of all numerical variables

![correlation](https://github.com/user-attachments/assets/8a440bce-647d-4adb-bc0f-a46476cd4a21)

*Scatterplot of Overall Cond vs Qual*

An interesting finding was the difference in correlation between Overall Condition and Overall Quality of the finish of the home. An accompanying plot is below this description.

Overall quality of finish was most highly correlated with Sale Price (.791) of all the variables. AN interesting finding was that overall condition of the finish was slightly negatively correlated (-.078) with Sale Price.

In short, this means the overall quality of materials used were more indicative of price direction than the actual condition of those materials. Looks like you might be better off getting the floor tiles from Italy in poor shape, over the cheaper tiles in great shape!

![cond_qual](https://github.com/user-attachments/assets/3c7be281-7f29-4116-bd19-44d71edd74e9)

*Engineered Features*

Two columns were added to the dataset for the model to look at -

1. Area Ratio - the ratio of living area square footage to lot square footage - higher number means more of the total lot is taken up by living space (rather than yard or non-living space)

2. Bed/Bath - the ratio of bathrooms to bedrooms

Neither of these showed a strong correlation either way to the target, but were left in the dataset for the model's use

### 3c - Preprocess Data for Model <a name="preprocess-data-for-model"></a>
*[Click here](Notebooks/khp-train3.ipynb) to jump to the notebook containing preprocessing and model training*

Data was preprocessed according to above outline with the intention of running through a linear regression and decision tree model. Decision tree ideal depth was determined with a grid search cross validation. Pipelines were created to ensure no data leakage and ensure reliable copying of model

### 3d - Model Prediction/Analysis <a name="model-prediction/analysis"></a>

In the end, the linear regression scored the highest at around 0.16 log RMSE. Though this was short of the target, there is room for improving upon the current models. Will also search for models to use other than decision tree or linear regression to find a better source of predictions.


## 4 - Next Steps <a name="next-steps"></a>

1. Create joblib file to save models fit. This will allow cleaner presentation with a separate notebook each for pipeline and model management, rather than a single notebook like it is now.
2. Try different methods for cleaning and encoding data, to try and improve model predictions
3. Try out various other models, along with cleaning methods address above, to get the final log RMSE below .13897

## References <a name="references"></a>

*Map of Ames, Iowa* - <a href="https://commons.wikimedia.org/wiki/File:Ames_map.png">PeryPlanet</a>, Public domain, via Wikimedia Commons











