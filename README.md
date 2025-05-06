# Section A – Open Source Data Science Project
## Formula 1 Predictions using 1950-2024 dataset

## Executive Summary
This project aims to predict the next Formula 1 Drivers' World Champion using a logistic regression model. The model achieves a balanced accuracy of 66.67% and an F1-score of 50. Key predictors identified include Constructor Overall Win Percentage, Constructor Form, and Driver Win Percentage in the previous season. These insights offer a compelling perspective on the sport's competitiveness in the modern era.

## Research Question
What are the key predictive features of the Formula 1 Drivers' World Championships, and can these features predict the next winner of the Drivers' World Championships?

## Introduction
This project explores the sport of Formula 1 to identify key predictive features for the Drivers' World Championship. By analysing historical data, the study aims to determine the factors most significantly influencing championship outcomes. The logistic regression model developed will predict the next Drivers' World Champion, providing insights into modern Formula 1 competitiveness. The project draws inspiration from (Bell et al. 2016).

## Data Infrastructure and Tools
SQL was used to create the final data table due to its efficiency in handling large datasets and interacting with relational databases for quick querying, filtering, and aggregation. SQL coding was conducted in Microsoft Access for its compatibility and ability to output CSV files for use in Python. Python was chosen for data analysis due to its versatility and powerful libraries like pandas. Although Power BI was considered, Python was preferred for its ability to handle complex analysis, with SQL used for the majority of data engineering. *All python code created for this project was done so in Google Colab and can be found within the github branch. See ['F1_logistic_regression_Modern_Era.ipynb']([https://github.com/gregjohnallen-52/Open-Source-Data-Science-Project/blob/main/F1_2025_predictions.ipynb](https://github.com/gregjohnallen-52/Open-Source-Data-Science-Project/blob/main/F1_logistic_regression_Modern_Era.ipynb)) and ['F1_2025_predictions.ipynb'](https://github.com/gregjohnallen-52/Open-Source-Data-Science-Project/blob/main/F1_2025_predictions.ipynb).*

## Data Collection
Data for every year of the Formula 1 World Championship ranging from 1950 – 2024 was sourced from Kaggle. (Formula 1 World Championship (1950 - 2024) n.d.)
The dataset includes race results, sprint races, qualifying sessions, and standings for Constructors' and Drivers' Championships, along with constructor and driver details, lap times, and pit stop times. Critical variables include race wins, podiums, previous results, championships, races entered, and finishing positions.

## Data Engineering
Relevant tables were selected to minimise data loading and calculation times. The final tables used from the dataset were; constructor_standings.csv, constructors.csv, driver_standings.csv, drivers.csv, races.csv, results.csv, and seasons.csv.
The selected tables were merged in SQL with calculated columns added to produce the final output, ready for analysis.  
Figure 1: SQL Queries for calculated fields for use in final output.
 
Figure 2: SQL Creation of final output table
The final output includes the following aggregated values:
•	Wins and podiums in the previous season, and in total. 
•	Champion in the previous season.
•	Form based on average position over previous five seasons.
•	Boolean indicator of winning the championship.
•	Number of races entered.
These aggregates include elements of recent form and historical performance, allowing the model to be influenced by current form, experience, and historical success. Wins and podiums will be converted to percentages by season and overall in Python to balance the dataset across different eras.

An overview of the output table is available in Appendix A. 

 
Figure 3: Initial assessment of dataframe loaded into python.
 
Figure 4: Data Cleansing Steps undertaken in Python.
 
Figure 5: Data Aggregation Steps in Python.

## Data Analysis
Exploratory Data Analysis (EDA) was performed to identify the coefficients of variables for the model. A logistic regression model was developed using historical season results to predict whether a driver will win the championship in the subsequent season. These methods were chosen for their ability to offer clear, interpretable insights into complex datasets and their effectiveness in predicting outcomes based on historical data.

 
## Figure 6: Sample of EDA performed in Python.
 
Figure 7: Balance assessment of dataset.
The figure shows that the dataset is unbalanced with regards to the outcome of ‘DriverWonChampionship’. Solutions were considered to deal with this issue: 
•	to create synthetic data with minority outcomes, potentially affecting model accuracy. (Tri Suci, Sari Hasibuan, and Pane 2022)
•	Class Weight Adjustment, to assign a higher weight to the majority outcomes. 
•	Ensemble Methons such as Random Forest or Gradient Boosting. 
Although oversampling is a common practice, its justification is not well explained(Salas-Eljatib et al. 2018). Given the inherently unbalanced nature of Formula 1 outcomes, it was decided to proceed with the unbalanced dataset, as no resampling technique could guarantee improved model performance (Ke et al. 2024).
To create a more balanced dataset and focus on the 'Modern Era' of F1, data from seasons before 2010 was excluded, aligning with the introduction of the current points scoring system.
 
Figure 8: Dropping data for all seasons before 2010 and new visual displaying a more balanced, but still unbalanced, dataset.
Although the dataset is still unbalanced, it is more balanced, moving from a ratio of over 45:1 majority to minority, to under 23:1. This helps balance the dataset without changing the integrity of the dataset and results. 

The dataset is now prepared for a logistic regression model to be created. 
 
Figure 9: Creation of Logistic Regression Model
 
Figure 10: Model Assessment in Python
 
Figure 11: Further Model Assessment in Python
 
Figure 12: Model Coefficients in Python
 
Figure 13: Intercept and Coefficients in Python.

## Results
The results that the model achieved demonstrate that the model is working and gives results in the area to be expected, taking into account the unbalanced nature of the dataset. 
In Figure 10 the accuracy of the model is given at 97.2%, a balanced accuracy of 66.67% and an F1-score of 50.0.
In Figure 11 we can see the ROC curve for the model with an Area Under the Curve (AUC) of 0.67.
In Figure 12 we can see the coefficients of each of the variables used in the final model and Figure 13 gives the intercept of the model. 

 
Figure 14: Final Equation of logistic regression model.
Using this equation we can predict the winner of the 2025 drivers world championship be creating a dataset containing all the same statistics of the 2025 drivers and applying this formula to them. The 2025 drivers dataset was created as a csv file, run through the same python data engineering steps and then subjected to the final model equation. Which gives the results in Figure 15, below. 

 
Figure 15: 2025 Drivers  logit_p outputs

## Discussion
Figure 10 shows the model's accuracy at 97.2%, indicating high predictive performance (Classification: Accuracy, Recall, Precision, and Related Metrics | Machine Learning n.d.). However, in imbalanced datasets, accuracy can be misleading as it may reflect the majority class. The balanced accuracy of 66.67% provides a more realistic measure, highlighting difficulty in predicting the minority class but still above the 50% expected by chance.

The F1-score for the true class is 50.0, indicating struggles with precision and recall for the minority class  (Géron 2022). The confusion matrix in Figure 11 shows correct predictions for all negative outcomes but struggles with positive outcomes, correctly predicting only one winner out of three seasons, resulting in false negatives. 

Figure 11's ROC curve shows an AUC of 0.67, indicating moderate performance (Cuantum Technologies LLC 2025). Figure 12 highlights reliance on the constructor's historical win percentage and recent form, with less importance on driver wins and constructor podiums in the previous season. Surprisingly, the model assigns strong negative importance to cumulative championships won by both driver and constructor, contrary to expectations.

Figure 15 shows the model predicted no clear winner for the 2025 season, classifying Norris as the most likely winner, with Verstappen and Piastri also in contention. Some results are questionable, such as Hamilton being least likely despite being at a competitive Ferrari team, and rookie drivers like Bearman being highly rated. This suggests an imbalance in handling rookie drivers, indicated by the negative impact of cumulative championships in Figure 14.

## Potential Improvements
Extending the dataset to include more historical data could enhance the model's predictive power, ensuring a balanced representation across different eras of the sport. Replacing the average position, which negatively correlates with performance, with the number of points achieved in a race could improve accuracy, though historical races would need the modern points system applied for consistency. Broadening the dataset to include variables such as fastest laps and qualifying positions would provide a more comprehensive analysis.

The model's handling of new drivers and constructors could be improved. Including youth career statistics for new drivers, though limited to recent rookies, would be beneficial. Constructors should not be treated as new entries when rebranded; linking teams like Renault and Alpine, or RB/Torro Rosso/Alpha Tauri, to a consistent constructorId would ensure their historical performance is considered.
 
## Horizon Scanning
Exploring alternative methods such as Random Forest or Gradient Boosting could provide more robust predictions for unbalanced datasets (7 Techniques to Handle Imbalanced Data n.d.). Random Forest combines multiple decision trees to improve accuracy and control over-fitting, handling large datasets with higher dimensionality and capturing complex interactions between variables. Gradient Boosting Machines (GBM) are also effective for imbalanced datasets, offering high predictive performance.

In the context of Formula 1, AI and Machine Learning are increasingly integral to the sport's evolution. Teams leverage these technologies for various applications, from tyre wear analysis to optimising race strategies (Brittle 2024). AI's role in F1 extends to areas such as broadcasting, sustainability, and enhancing race performance (Marr n.d.). For instance, AI-powered simulations model billions of potential race parameters to determine favourable outcomes. As AI technology matures, its influence on motorsport will likely expand, making the sport faster and fairer (Could AI Make F1 Faster and Fairer 2025).

## License
It was vital that the data that was sourced for the analysis was available for use and, if required, permission was obtained for the data to be used in the project before the work could begin. The data used in this project has no copyright and has made the data available in the public domain. (Deed - CC0 1.0 Universal - Creative Commons n.d.) 

## References

7 Techniques to Handle Imbalanced Data (n.d.) available from <https://www.kdnuggets.com/7-techniques-to-handle-imbalanced-data> [2 May 2025]
Bell, A., Smith, J., Sabel, C.E., and Jones, K. (2016) Formula for Success: Multilevel Modelling of Formula One Driver and Constructor Performance, 1950-2014. 
Brittle, C. (2024) ‘AI in Formula One: What Role Is the Technology Playing in Race Strategies, Broadcasts and Sustainability?’ [2 September 2024] available from <https://www.blackbookmotorsport.com/features/f1-ai-machine-learning-race-strategy-broadcast-aws-sustainability-driverless-cars-oracle/> [2 May 2025]
Classification: Accuracy, Recall, Precision, and Related Metrics | Machine Learning (n.d.) available from <https://developers.google.com/machine-learning/crash-course/classification/accuracy-precision-recall> [2 May 2025]
Could AI Make F1 Faster and Fairer (2025) available from <https://www.raceteq.com/articles/2025/01/could-ai-make-f1-faster-and-fairer> [2 May 2025]
Cuantum Technologies LLC (2025) Machine Learning Hero [online] available from <https://learning.oreilly.com/library/view/machine-learning-hero/9781837025015/> [2 May 2025]
Deed - CC0 1.0 Universal - Creative Commons (n.d.) available from <https://creativecommons.org/publicdomain/zero/1.0/> [2 May 2025]
Formula 1 World Championship (1950 - 2024) (n.d.) available from <https://www.kaggle.com/datasets/rohanrao/formula-1-world-championship-1950-2020> [2 May 2025]
Géron, A. (2022) Hands-On Machine Learning with Scikit-Learn, Keras, and TensorFlow, 3rd Edition [online] available from <https://learning.oreilly.com/library/view/hands-on-machine-learning/9781098125967/> [2 May 2025]
Ke, J.X.C., DhakshinaMurthy, A., George, R.B., and Branco, P. (2024) ‘The Effect of Resampling Techniques on the Performances of Machine Learning Clinical Risk Prediction Models in the Setting of Severe Class Imbalance: Development and Internal Validation in a Retrospective Cohort’. Discover Artificial Intelligence 4 (1), 91
Kwak, S. and Kim, J. (2017) ‘Statistical Data Preparation: Management of Missing Values and Outliers’. Korean Journal of Anesthesiology 70, 407
Marr, B. (n.d.) How Artificial Intelligence, Data And Analytics Are Transforming Formula One In 2023 [online] available from <https://www.forbes.com/sites/bernardmarr/2023/07/10/how-artificial-intelligence-data-and-analytics-are-transforming-formula-one-in-2023/> [2 May 2025]
Salas-Eljatib, C., Fuentes-Ramirez, A., Gregoire, T.G., Altamirano, A., and Yaitul, V. (2018) ‘A Study on the Effects of Unbalanced Data When Fitting Logistic Regression Models in Ecology’. Ecological Indicators 85, 502–508
Tri Suci, A., Sari Hasibuan, M.N., and Pane, R. (2022) ‘(PDF) Comparative Analysis of Resampling Techniques on Machine Learning Algorithm’. ResearchGate [online] available from <https://www.researchgate.net/publication/367709819_Comparative_analysis_of_resampling_techniques_on_Machine_Learning_algorithm> [1 May 2025]

## Appendix A


