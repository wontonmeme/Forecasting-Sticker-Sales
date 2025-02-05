Dataset Link: https://www.kaggle.com/competitions/playground-series-s5e1

# Project Summary:
The dataset is generated from the Kaggle playground series, it provides different datasets monthly for the community to practice their machine learning and modelling skills. In this Challenge the purpose
was to attempt to Predict Sticker Sales. To gain experience and learn from others, I read through the discussions and looked at the different codes brought by different people from the community.
This gave me enough ideas to start, branch off later, and do my own thing. 

I started with creating a simple Light Gradient Boosting Machine (LGBM) model. With the model, I got a poor score. I struggled to get a good score because I forgot about the various benefits that the Box-Cox or Log transform can provide in improving models. 
After the fact, I felt pretty dumb since I had used the Box-Cox in projects for school before. When I realized this, I used it to create what would eventually be the LGBM model provided in this repository.

Afterwards, I used ridge regression with a grid search to find the best l1 and l2 parameters.

Since I didn't want to just copy and paste the best model posted, my desire to create a better model led me to watch a time series Crash Course by Egor Howell. Through it, I learned the use of Seasonal Autoregressive
Moving Averages with Exogenous Variables (SARIMAX). With this in mind, I saw that through auto-correlation and partial auto-correlation plots, I noticed that there was a yearly seasonality for certain products and a two-year seasonality for other products. There were also,
good time lag picks of 7 and 1 day lags. So with this information, I separated the data into 90 different datasets by the categorical data given and created SARIMAX models for all. This is what led me to create the SARIMAX model posted here. From then on, I decided to try to combine models
through a public model and mine to see the results. Not surprisingly, it gave me my best score in the competition.

Final MAPE Scores on Kaggle:
| Model | MAPE Score
|-------|-------
| SARIMAX | 0.11783
| LGBM | 0.11952
| Elastic Net | 0.11654
| SARIMAX plus public model | 0.9086

When I compare my Scores to the leaderboard, my worst score would put me above 79% of the 2723 participants.

## Data Information
| Data | Description
|------|------------
| id | self explanatory
| country | Countries are Canada, Finland, Italy, Kenya, Norway, and Singapore
| store | Stores are Discount Stickers, Stickers for Less, and Premium Sticker Mart
| product | Products are Holographic Goose, Kaggle, Kaggle Tiers, Kerneler, Kerneler Dark Mode
| num_sold | The value I attempted to predict, which is the number of stickers sold

Beyond this, I also included and used the yearly GDP data from worldbank.org
