# BostonAirbnb

In this project, I have downloaded a Boston Airbnb file from Kaggle https://www.kaggle.com/datasets/airbnb/boston.

First, data was cleaned. 
1. I skipped descriptive columns which requires NLP. 
2. Amenities such as TV, Internet, AC and free parking are deemed important for pricing; therefore, those are extracted into boolean columns. 
3. Occupancy is calculated from availabiity_30 column, which should be also an important factor for pricing. 
4. Numerical columns were imputed with means. 
5. Other categorical columns were also converted into one hot encoding.