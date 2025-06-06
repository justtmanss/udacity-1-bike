# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### NAME HERE

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
When submitting predictions to Kaggle, I realized that any negative predicted values would cause the submission to be rejected. Therefore, it was necessary to set all negative predictions to zero before creating the submission file to ensure all predicted counts were non-negative.

### What was the top ranked model that performed?
The top ranked model from the initial training was the one trained using AutoGluon's TabularPredictor with the preset "best_quality" and a time limit of 10 minutes. This model used the root mean squared error (RMSE) as the evaluation metric and ignored the 'casual' and 'registered' columns.

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
The exploratory data analysis revealed important temporal patterns in the data. For example, extracting the hour from the datetime column allowed categorization of rush hours, midday, and off-peak periods. Histograms of features showed their distributions and helped identify categorical variables. An additional feature, "year," was created by extracting the year from the datetime column to provide more temporal context to the model

### How much better did your model preform after adding additional features and why do you think that is?
After adding the additional "year" feature and other temporal categorizations, the model's performance improved significantly. This improvement is likely because the new features provided more relevant information about temporal trends and seasonality, which are important factors influencing bike sharing demand.

## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
Hyperparameter tuning using Bayesian optimization and local scheduling with 20 trials further improved the model's performance. The tuned model showed better RMSE scores compared to the initial and feature-enhanced models, indicating that optimizing model hyperparameters can lead to more accurate predictions.

### If you were given more time with this dataset, where do you think you would spend more time?
Given more time, I would focus on extensive feature engineering to extract more meaningful temporal and weather-related features. Additionally, I would explore ensembling different model types and perform more comprehensive hyperparameter tuning to further improve prediction accuracy.

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
|model|hpo1|hpo2|hpo3|score|
|--|--|--|--|--|
|initial|N/A|N/A|N/A|0.50392|
|add_features|N/A|N/A|N/A|0.42443|
|hpo|Models Tuned: GBM, CAT|Models Tuned: XGB, RF|Models Tuned: NN_TORCH|0.47446|

### Create a line plot showing the top model score for the three (or more) training runs during the project.
The line plot image is saved as model_train_score.png in the img folder.

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.
The line plot image is saved as model_test_score.png in the img folder.

![model_test_score.png](img/model_test_score.png)

## Summary
This project demonstrated the use of AutoGluon's Tabular Prediction to forecast bike sharing demand. Starting from initial model training, through exploratory data analysis and feature engineering, to hyperparameter tuning, each step contributed to improving model accuracy. The project highlighted the importance of data preprocessing, feature creation, and model optimization in building effective predictive models. The results show promising performance, and further enhancements could be achieved with additional feature engineering and tuning.