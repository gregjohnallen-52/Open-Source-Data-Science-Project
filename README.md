# Formula 1 Predictions using 1950-2024 dataset

## Research Question
What are the key predictive features of the Formula 1 Drivers' and Constructors' World Championships, and can these features predict the next winner of the Drivers' and Constructors' World Championships?

## Executive Summary
This project aims to predict the next winner of the Formula 1 Drivers' and Constructors' World Championships by developing a logistic regression model. The model is designed to identify the next Drivers' World Champion with an accuracy of X% and the next Constructors' World Champion with an accuracy of X%. By analysing the results and statistics from the past five years, key predictors such as X, X, and X have been identified. The insights derived from the model offer a compelling perspective on the competitiveness of the sport in the modern era.

## Introduction
This project delves into the competitive realm of Formula 1, aiming to uncover the key predictive features that determine the winners of the Drivers' and Constructors' World Championships. By examining the results and statistics from the past five years, this study seeks to identify the factors that most significantly influence championship outcomes. The development of a logistic regression model will facilitate the prediction of the next Drivers' and Constructors' World Champions. This analysis is to gain an understanding of competitiveness in modern Formula 1 racing. Project takes inspiration from (Bell et al. n.d.)

## Methods
### Data Collection
• Source: Data for every year of the Formula 1 World Championship ranging from 1950 – 2024 was sourced from Kaggle. - [F1 Data Source](https://www.kaggle.com/datasets/rohanrao/formula-1-world-championship-1950-2020/data "F1 Data Source")  
• Data: The dataset contains results from each race, sprint race, and qualifying session, as well as the final standings of each season's Constructors' and Drivers' Championships.  
• Variables: Critical variables include race wins, starting position, previous years' results, number of races, and other relevant metrics. (To be expanded)  
• Data Preparation/Cleaning: The data was checked for missing values, outlier analysis was conducted to ensure data quality, merging of tables.  

### Data Analysis
• Techniques Used: Exploratory Data Analysis (EDA) was conducted to determine coefficients and select variables to be used in the model. A logistic regression model was developed using the results from the previous five seasons to predict whether a driver or team will win the championship in the following season. Python was utilised for the implementation of these techniques.  
• Justification of Methods: These methods were selected for their ability to provide clear, interpretable insights into the complex datasets and their effectiveness in predicting outcomes based on historical data. Python was used for its versatility and powerful libraries, such as pandas for data manipulation. Python's extensive ecosystem and ease of use make it ideal for performing data science projects efficiently and effectively.  
• Figures: Extracts of code will be shown, along with data visualisations of results over the seasons and of the model in use.  

## Results
• Data Communication Tools: Visualisations were created using Power BI interactive dashboards.  
• Figures: These include trends of points, wins, fastest laps, and other relevant metrics. (To be expanded)  
• Model Outputs: The final formula of the logistic regression model, along with the accuracy achieved, confusion matrix, ROC Curve, and a bar chart showing the coefficients' importance.  

## Discussion/Recommendations
• Model Performance: The logistic regression model demonstrated a high level of accuracy in predicting the winners of the Drivers' and Constructors' World Championships, as evidenced by the achieved accuracy metrics, confusion matrix, and ROC Curve. The model's insights into the key predictive features provide valuable understanding of the factors influencing championship outcomes. (To be adjusted based on results of model)  
• Potential improvements  
  o Normalisation of Points Systems: Adjust the points systems to account for changes over different seasons to ensure consistency in the data.  
  o Extension of Dates Used: Expand the dataset to include more historical data, which could enhance the model's predictive power.  
  o Normalisation of Number of Races: Standardise the number of races per season to account for variations across different years.  
  o Broaden Dataset: Include additional variables such as fastest laps, sprint races, and other relevant metrics to provide a more comprehensive analysis.  
