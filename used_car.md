### Used-Car Price Prediction ML Model: Comparing Linear Regression, Ridge, and Lasso
For a UC Berkeley ML & AI assignment, I compared three models using 38 vehicle features to estimate listing prices.

The models predicted log price—a compressed scale for handling a wide range of prices. On the current test split, they explained about 60% of the variation in log prices. Their results were nearly identical, and Lasso kept all 38 features.

To see which data the model relied on, I shuffled one feature at a time and measured the change in its score. Vehicle age had the largest impact, followed by fuel_gas and mileage_per_year. This shows what the model used to predict; it doesn’t show that those features cause prices to change.

I also found a problem in the evaluation: manufacturer and state price averages were calculated using all listings before the train/test split. That let test-price information influence the features, so the test set wasn’t fully unseen. I’m recalculating those averages from training data only and will rerun the evaluation before treating the scores or feature rankings as final.

For me, the ML engineering lesson is clear: validate the data path before trusting the model score.

Project: https://github.com/patisankar/uc-car_price_prediction_project
