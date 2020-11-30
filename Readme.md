# Project 2: Ames Housing Data and Kaggle Challenge

## Problem Statement
I am a data scientist working at the Central Iowa Board of Realtors, based in Ames, Iowa. My employer wants me to analyze data from houses sold in 2006 to 2010 in order to model how the features of a house effect it's sale price, and then to teach the realtors what my model predicts. As a test of the model, I will run it on a dataset of houses with unknown sale prices.

## Executive Summary
I am setting out to answer the following questions for the Central Iowa Board of Realtors:
- Which features appear to add the most value to a home?
- Which features hurt the value of a home the most?
- Which features make no difference to the value of a home?
- What can be changed about a home to increase the value?
- What data would I need to generalize this model to other cities and other time periods?

## Contents
- Exploratory Data Analysis and Exploratory Visualizations
- Data Cleaning
- Pre-Processing
- Repeat Loading Data, Data Cleaning, Pre-Processing, and Saving Results for Test Dataset
- Set Up X and Y, and Training and Test Data
- KNN Regression
- Ridge Regression
- Lasso Regression
- Visualizations
- Apply Model with Best Score to Test Data to Predict the Sale Prices, Drop Extra Columns, and Save Model and Predictions

## Data Dictionary for Interaction Features and Polynomial Features
**All features are scaled and label encoded for the analysis.**

|Feature|Description|Reasoning|
|---|---|---|
|**Exterior Combined**|First Exterior Covering on the House times Second Exterior Covering on the House|These features are collinear since a house can't have a second covering without a first, so the original features were dropped. Certain coverings pair well (e.g., wood and brick) so the interaction term was kept.|
|**Rooms Combined**|Above Ground Living Area times Total Rooms Above Ground|These features are collinear since larger above ground living area corresponds to more rooms, so the original features were dropped. A house with a larger area and larger rooms would increase the price (e.g. more than just more rooms with the same area) so the interaction term was kept.|
|**Fireplace Combined**|Number of Fireplaces times Fireplace Quality|The features are collinear since houses with more fireplaces also tend to be large and have well-maintained fireplaces, so the original features were dropped. A house with many well-maintained fireplaces will have higher price, so the interaction term was kept.|
|**Garage Combined**|Garage Car Capacity times Garage Size times Garage Quality times Garage Condition|These features are collinear since larger garages tend to fit more cars, be built with higher quality, and be in better condition, so the original features were dropped. A house with a combination of these factors would fetch a higher price, so the interaction term was kept.|
|**Pool Combined**|Pool Area times Pool Quality|These features are collinear because a homeowner with a large pool can likely afford to maintain it well, so the original features were dropped. A large, well-maintained pool increases house price, so the interaction term was kept.|
|**Bsmt Type 2 Combined**|Secondary Basement Area Finish times Secondary Basement Area Size|These features are collinear because the larger basements tended to have a particular finish, so the original features were dropped. A large basement area with a nicer finish increases house price, so the interaction term was kept.|
|**Year Combined**|Year Built times Garage Year Built|These features are collinear because newer houses had newer garages, so the original features were dropped. A new house with a new garage increases the house price, so the interaction term was kept.|
|**Year Built Squared**|Square of Year House Was Built|An increase in the year built increased price more for newer houses, so a squared term was added to account for this uptick.|
|**Year Remod/Add Squared**|Square of Year House Was Remodeled|An increase in the year remodeled increased price more for newer houses, so a squared term was added to account for this uptick.|
|**Garage Yr Blt Squared**|Square of Year Garage Was Built|An increase in the year the garage was built increased price more for newer houses, so a squared term was added to account for this uptick.|


## Business Recommendations
- Which features appear to add the most value to a home?
    - Above ground living area times total rooms above ground
    - Overall quality of the home
    - Square footage of main finished area of basement
    - Total square footage of basement
    - Area of masonry veneer on home
    - Area of lot
    - Quality of exterior
    - Square footage of first floor
    - Square footage of second floor
    - Garage car capacity times the garage size times the garage quality times the garage condition
- Which features hurt the value of a home the most?
    - Bedrooms above ground, if there aren't more total rooms above ground
    - Basement condition, unless that basement has high quality, good light exposure, and large size
    - Kitchens above ground, unless those kitchens are high quality
    - Building type
    - Land contour
    - House style
    - Roof material
    - Newer houses were cheaper in this dataset due to the 2009 recession
    - Pool area times pool quality, possibly because larger pools fit in rural, cheaper areas
    - Zoning
- Which features make no difference to the value of a home?
    - Year built times garage year built
    - Primary basement area finish
    - Number of bathrooms in the basement
    - Porch area
    - Unfinished basement area size
    - Classification of house
    - Year remodeled, except the amount covered in the year remodeled square term
- What can be changed about a home to increase the value?
    - Increase the overall quality
    - Finish the basement
    - Add masonry veneer
    - Increase exterior quality
    - Increase garage quality
- What data would I need to generalize this model to other cities and other time periods?
    - Longer time period of data to show multiple economic swings
    - Other cities, to compare the priorities for the homebuyers in those cities to Ames, IA
