# Predicting Covid-19 Infections


Check out how I walk through my code on my YouTube Channel: https://www.youtube.com/watch?v=pr1Su6IHHmI&t=286s


	Introduction
This project aims to investigate if COVID-19 symptom searches on Google can predict new infections with the virus in the United States. With the ongoing pandemic, forecasting new COVID-19 infections could be extremely valuable to everyone, especially legislators, companies, and high-risk individuals. Predicting the numbers of new infections is very intricate and complicated because the virus and its spread is not entirely clear since it has been discovered only recently and not much research has been established. The underlying assumption and hypothesis for this project is that if people experience symptoms of COVID-19, they will use Google to find out if their symptoms match the criteria for COVID-19 symptoms. People experiencing symptoms and searching for them on Google will then go on to get tested positive for the Coronavirus. If this assumption holds, COVID-19 searches on Google can have predictive power to forecast new infections across the US.
	Methods and Data
To investigate the relationship between COVID-19 Google searches and new infections, a linear regression model is used. The relationship between the Google searches and new infection cases ought to be linear, hence no other transformations are increasing the predictive power of the model. The following graph depicts the relationship between the keyword “Covid symptoms” and new infections in the US, according to the CDC.

![Linear Model Covid Symptoms vs New Infections Scatterplot](scatterplot.png)

The linear relationship between the Google Trend popularity index (on a scale from 0-100) and new COVID-19 is clearly linear and an OLS model should allow us to draw a picture of the relationship between symptom related searches and new cases.
Google allows its search trend data to be filtered and exported. This project uses Google’s Python Collaboratory tool to pull the data from Google trends and transform it into the right data frame to run OLS regressions. The advantage of this method is that the data timeframe can be adjusted quickly when rerunning the script to validate the model. The new COVID-19 infection data is downloaded from the CDC Covid Data Tracker which is daily updated data and considered the most reliable source for this kind of data. The data was aggregated into weekly data to make a comparison easier and more reliable. Google Trend data is instant, whereas the new COVID-19 infections data is delayed due to the time lag from testing and reporting the numbers. Therefore, using a time lag of a week (t-1) has shown to yield the best regression models.

	Results and Efficacy
The results of the regression emphasize the strengths and weaknesses of the model and the assumption behind it. The regression is able to predict 91.1% (Adjusted R Square) of the variation in new COVID-19 cases. According to this model, new COVID-19 cases are a function of the Google Trend searches “Cough”, “Fever”, “Headache”, “Diarrhea”, and “Covid Symptoms”.


COVID-19 Cases = β_(0 )+"Cough"*X_1+"Fever"*X_2+"Headache"*X_3+"Diarrhea"*X_4+〖"Covid Symptoms"*X〗_5

| Predictive Variable | Coefficients|
|---------------------|:-----------:|
| Cough	      	      |    41,370   |
| Fever               |   -42,860   |
| Headache 	      |    29,980   |
| Diarrhea	      |	  -31,060   |
| Covid Symptoms      |    13,990   |

The keywords are the most common symptoms for COVID-19, established by the CDC. The term “Covid Symptoms” is presumably a popular query to find out if an individual has symptoms that point towards the Coronavirus and should therefore get tested. The results of the regression show that the keywords “cough”, “headache”, and “Covid Symptoms” are positively correlated with new cases, whereas the keywords “fever” and “diarrhea” are negatively correlated. Notably, all coefficients are statistically significant at the traditional confidence levels, except for “headache” which is significant at the 5% level. This suggests that the predictors are meaningful to explain the variation in the model. However, the negative coefficients of the keyword “cough” and “fever” indicate that for every unit change in the Google Trend index, new COVID-19 cases decrease by 42,860 and 31,060, respectively. This result goes against the heuristic that with an increase of Google searches for the symptom, COVID-19 cases increase. Hence, the initial assumption ought to be reevaluated and an alternative model can be developed. Nevertheless, the regression can be used to predict new infections and can explain a very large portion of the variation in the data. To predict new COVID-19 cases for Monday, December 14th, 2020, Google Trend numbers from 7 days before this date can be used in the model. In this case, the Google index values for the symptom keywords from Monday,  December 7th are predicting cases for the following week.


〖COVID-19 Cases〗_(12-14-2020 )= β_(0 )+"Cough"*26+"Fever"*40+Headache*32+Diarrhea*26+Covid Symptoms*92


This model yields a prediction of 179,461 cases for Monday, December 14th, 2020.


	Conclusions
The model is a good predictor of new COVID-19 infections and explains 91.1% of the variation. However, it does not confirm the initial assumption of a positive relationship between the predictors and the outcome. Conclusions for causality between the Google Trend searches, and the predicted new cases cannot be drawn. The model’s omitted variable bias only allows to create relationships of association and predictions ought to be treated and interpreted accordingly. Other factors and omitted variables and circumstances can lead to a completer and more sophisticated model. It is worth noting that the longer the pandemic lasts, the more likely the general population is aware of the symptoms and therefore less likely to search Google when they develop the symptoms. Concluding, this project predicts COVID-19 cases with some limitations and needs more work to explore the relationship between Google Trend searches and real world COVID-19 trends further.
