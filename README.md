# Ames, Iowa Housing Data

<a title="PeryPlanet, Public domain, via Wikimedia Commons" href="https://commons.wikimedia.org/wiki/File:Ames_map.png"><img width="512" alt="Ames map" src="https://upload.wikimedia.org/wikipedia/commons/thumb/2/2c/Ames_map.png/512px-Ames_map.png?20121117200554"></a>

## Table of Contents

1. [Introduction](#introduction)
2. [Data](#data)
3. [Process Outline](#process-outline)
   1. [Clean Data](#clean-data)
   2. [Analyze Data](#analyze-data)
   3. [Preprocess Data for Model](#preprocess-data-for-model)
   4. [Model Prediction/Analysis](#model-prediction/analysis)
4. [Next Steps](#next-steps)
5. [References](#references)

## 1 - Introduction <a name="introduction"></a>

A client Pillo Corp. wants to create a model that will help them successfully predict the sale price of a house for their website. They're juding the success of a model based on the RMSE of the log(target) and log(predictions) of the model. They want this number to be 0.13897 or lower to be considered a success.

## 2 - Data <a name="data"></a>
The dataset we're working with is a list of houses from the Ames, Iowa region. Each row in the set is a property with 80 different unique features. Details about features of interest will be discussed in more detail throughout the process outlined below.

## 3 - Process Outline <a name="process-outline"></a>
Dataset needed to be cleaned up to fit into machine learning model. On initial inspection, care needs to be taken before removing info as there are only 1480 rows.

### 3a - Clean Data <a name="clean-data"></a>
[Test Link](data_description.txt)

### 3b - Analyze Data <a name="analyze-data"></a>

### 3c - Preprocess Data for Model <a name="preprocess-data-for-model"></a>

### 3d - Model Prediction/Analysis <a name="model-prediction/analysis"></a>

## 4 - Next Seps <a name="next-steps"></a>

1. Create joblib file to save models fit. This will allow cleaner presentation with a separate notebook each for pipeline and model management, rather than a single notebook like it is now.
2. Try different methods for cleaning and encoding data, to try and improve model predictions
3. Try out various other models, along with cleaning methdos address above, to get the final log RMSE below .13897

## References <a name="references"></a>

*Map of Ames, Iowa* - <a href="https://commons.wikimedia.org/wiki/File:Ames_map.png">PeryPlanet</a>, Public domain, via Wikimedia Commons










