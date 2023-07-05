# BostonAirbnb

In this project, I have downloaded a Boston Airbnb file from Kaggle https://www.kaggle.com/datasets/airbnb/boston.
In this study, I picked price as a target variable and the rest to predict the price for the property.

First, data was cleaned as follows:
1. I skipped descriptive columns which requires NLP. 
2. Amenities such as TV, Internet, AC and free parking are deemed important for pricing; therefore, those are extracted into boolean columns. 
3. Occupancy is calculated from availabiity_30 column, which should be also an important factor for pricing. 
4. Numerical columns were imputed with means. 
5. Other categorical columns were also converted into one hot encoding.

Then, I first used a simple linear model. But unfortunately, the model did not fit well to the data.
I employed XGBoost regressor and obtained reasonable results. 