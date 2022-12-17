# Project 2: Ames Housing Data & Kaggle Challenge


## Background

NexRes is a real estate agency in Ames with a portal that is highly trusted for its comprehensive market information on residential property in Iowa. NexRes helms over 40 real estate agents who assist people to buy and sell their homes. There is stiff competition in the Iowa real estate market, with more than 50 agencies vying for a slice of the pie. 

## Problem Statement

Nex Res, whose aim is to maintain its top status in the growing industry has activated its Data department to develop a data-driven solution to achieve their vision. Additionally, NexRes is a excellence-oriented and people-centred organisation, motivated to empower our agents to carry out their job.  To that end, the team has undertaken this project to predict the final price of each home with the lowest RMSE score possible via unique feature engineering and linear regression models such as Simple Linear, Ridge and Lasso.

The best model will help NexRes agents to advise clients on seeking fair valuations on their property, and as well as advise clients on actionable steps to take to reach their target price. NexRes agents are concerned with assisting homeowners who fall under two categories: those who are looking to sell, and those who are looking to buy. Agents want to provide top value to clients, who in turn want these questions answered:

* To what extent will renovations and/or remodeling give a good ROI (return of investment)? 
* Given a set list of desired features, what price range can they expect?
* Given a limited budget, which properties offer the most desired features?

## External Research

Ames is a city in Iowa, United States with a population of **66,424** as of 2021.<a href="https://www.census.gov/quickfacts/amescityiowa" target="_blank"><sup>1</sup></a> The city spans over 27 square miles, with a population density of **2,484 people per square mile**. Of the 23,866 households in the city, 41% of them are family dwellings.<a href="https://www.census.gov/quickfacts/amescityiowa" target="_blank"><sup>2</sup></a> Additionally, the average car ownership in Ames, Iowa is 2 cars per household.<a href="https://datausa.io/profile/geo/ames-ia/" target="_blank"><sup>3</sup></a>

The city has a humid continental climate <a href="https://www.weatherbase.com/weather/weather-summary.php3?s=6357&cityname=Ames,+Iowa,+United+States+of+America" target="_blank"><sup>4</sup></a>, where on average, the warmest records a daily mean of 74.0°F (or 23.3°C) and the coldest month records a daily mean of 20.4°F (or -6.44°C)<a href="https://www.usclimatedata.com/climate/ames/iowa/united-states/usia0026" target="_blank"><sup>5</sup></a> These are general characteristics of the population and the geography of Ames that gives us a glimpse into the patterns of real estate transactions in the city.


## Data Science workflow

In order to help NexRes agents answer the aforementioned questions, I fitted three different regression models to the housing data in order to determine the features that will most influence the sale price, and the features that are least influential as well. The performance of the models will be evaluated using the Root Mean Squared Error (RMSE). The RMSE is the square root of the variance of the residuals. It tells us how close the observed data points are to the model's predicted values, i.e, the absolute fit of the model to the data.

As the project deals with a significant amount of data, the coding work has been split into three Jupyter notebooks: 

* Data Cleaning, Exploratory Data Analysis (EDA) and feature engineering of the train data,
* Feature engineering of the test data, and
* Model fitting and Model evaluation

## Summary of Findings
A Lasso regression model had the best predictive performance on housing sale price in Ames USA among all the regression models tested. The model revealed which factors which are significant determiners of a property's sale price. With an r-squared value of  (0.808) and an RMSE of 34220.39, it can be used to predict house prices in Ames with relatively high accuracy based on characteristics of the house.

The features which are most influential on a property's sale prices are: overall quality of property, above grade living area, total square footage of basement, garage area, number of cars that fit in the garage, square footage of first floor, year house was built, the last year the house was remodelled/renovated, number of full baths,to name a few, based on the correlation coefficient with the sale price.

Property owners looking to sell can gauge the price their home can fetch, as well as plan out which enhancement features they should invest in to receive a target sale price. Meanwhile, property owners looking to buy can use the trained model to predict the features of their future home given their current budget.

## Limitations

However, the model is rather limited as it was developed using data collected on properties sold between 2006 - 2010. Furthermore, the dataset only captured the real estate transactions in Ames, Iowa. As the dataset is limited in terms of both the time frame, it could not capture any year-to-year changes in property sale prices as the economy recovered from the 2007-2009 economic recession, as well as price changes due to inflation. In addition, as the dataset is specific to Ames, the model will not work reliably on forecasting prices of properties in other locations without the location-specific data. In addition, the dataset also does not provide any insight into other possibly influential factors, such as proximity to recreation centres, business districts and education institutions that can also affect a property's valuation and hence its sale price.

All in all, property sale prices do not present an easy case to forecast as these are also affected by the economic climate, human sentiment, as well as other factors that cannot be captured by the data set. While there cannot be a perfect model, this project does prove to be a good proof of concept, and the model can be used to deploy an Application Processing Interface (API) that can serve as a minimum viable product. 


## Conclusions & Recommendations

There is no perfect model as building any machine-learning model necessitates dealing with the bias-variance trade-off. For this project, Lasso Regression was the best model according to RMSE scores. It inevitably traded some variance for bias, which ultimately lead to a smaller error overall. As the three models instantiated focused on only 6 features, future iterations of this project can experiment with nominal features such as exterior 1 or  masonry veneer type. More research into the data collection methods especially regarding the columns exterior 1 and exterior 2 can shed some light into how to quantify it appropriately to be fed into the eventual machine-learning model. The current dataset have marked a number of duplicate observations between the two columns (exterior 1 and 2), which obscured my initial intention to include it, as external research proved that exterior renovation can have significant impact on a property's resale value<a href="https://www.familyhandyman.com/list/which-exterior-renovation-adds-most-value/" target="_blank"><sup>6</sup></a>

In addition, the next iteration of this project can also explore the use of non-linear regression models for sale price prediction. As non-linear regression can fit a wider range of curves, there is a possibility of developing a model with a better fit than my efforts with linear regression techniques.

To find out the model's generalisability, further research is needed to capture more up-to-date data, from property markets aside from Ames, Iowa to shed light on how different economic situations and climates can influence house features and its sale prices.



## Data Dictionary
Official data dictionary: http://jse.amstat.org/v19n3/decock/DataDocumentation.txt
