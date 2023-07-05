## BostonAirbnb

#Business Understanding

In this study, using Boston Airbnb data, I picked price as a target variable and the rest to predict the price for the property. Following questions will be answered:
Question 1: What factors affect pricing of the properties?
Question 2: Are there any areas which have higher prices?
Question 3: Besides usual predictor such as number of bedrooms, are there any interesting observations?

#Data Understanding
In this project, I have downloaded a Boston Airbnb file from Kaggle https://www.kaggle.com/datasets/airbnb/boston. Each row of data consists of 95 columns such as price, cancellation policy, number of bedrooms, availabilities in the next 30 days, number of reviews and etc.

#Prepare Data
First, data was cleaned by removing descriptive columns such as description and summary, which require NLP. Also, some trivial columns such as id, name of the properties were dropped. However, amenities such as TV, Internet, AC and free parking are deemed important for pricing; therefore, those are extracted into Boolean columns. Also, occupancy is calculated from availabiity_30 column, which should be also an important factor for pricing. Numerical columns were imputed with means. Furthermore, other categorical columns were also converted into one hot encoding.

#Modeling
Now, it is time for creating a model. First, I made an attempt to create a linear model. However, the model returned not acceptable results. Namely, the r-squared score for the test model was -1.2855529833427669e+25 on 1076 values, and RMSE of the base model was 606597861038457.5.

Then, I decided to use XGBoost, which has gained popularity these days for tabular data regression model. The XGBoost model made a significant improvement over the linear model. The r-squared score for the train model was 0.2778078546927162 on 1076 values, and RMSE of the base model was 143.77463198930494.


#Question 1: What factors affect pricing of the properties?
I created an importance plot for the XGBoost model just created as seen in https://miro.medium.com/v2/resize:fit:1400/format:webp/1*Rs6cdeQ2SfmAM2P4HsdPbg.png. It is quite surprising that host response rate was the most important factor in pricing. However, host response rate might reflect levels of the hospitalities of the hosts. Number of bedrooms, bathrooms and occupancy were as expected.

#Question 2: Are there any areas which have higher prices?
To answer this question, I plotted a SHAP plot https://miro.medium.com/v2/resize:fit:1154/format:webp/1*jRtqva_as5pQ_A_bMbdVDw.png. The plot identified areas with higher prices such as Back Bay, Fenway, Downtown, Beacon Hill, and South Boston Waterfront.

#Question 3: Besides usual predictor such as number of bedrooms, are there any interesting observations?
Also, from the SHAP plot, TV and AC do not seem to affect pricing. 


#Conclusion
The linear model did not work well for the complex data such as Airbnb Boston. However, XGBoost did a fair job identifying key contributors to pricing of the properties, popular areas and something unexpected. The model can be further improved by employing NLP on descriptive data but this is time consuming and out of the scope of this simple analysis. I have also created a Medium blog post on this analysis. https://medium.com/@takahiko.koyama/creating-a-model-to-predict-price-of-airbnb-properties-in-boston-d140b3ed6f4