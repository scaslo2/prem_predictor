# Prem Match Predictor
Using Machine Learning, I created a model that can predict the Outcome of a Barclay's Premier League soccer (or football) match.

## Data Processing:
Using data (via Kaggle) from previous Premier League seasons, I developed my own key metrics that measure a team's home/away deffensive and offensive strength. Looking at our dataset, we see some non-numerical columns that need to be converted to values that can be processed and run through our model.
<br>

***It's important to note that the dataset is from the perspective of the home team***
<br>

First I have to convert the Results column to numerical values. I do this by creating a function called, transformResults. In our dataset, the results of each game are entered as either an "H" for a home team win or an "A" for an away team win. I use this function to convert any "H" into a value of 1, any "A" as a value of -1 and any draw becomes a value of 0.

    def transformResult(row):
      if(row.FTR == 'H'):
          return 1
      elif(row.FTR == 'A'):
          return -1
      else:
          return 0

Next we need to convert our Referee column. Considering how many different referees there are in the Premier League and the fact that we only need to address whether or not a referee was the ref at any one game, then the best option would be to convert each category value into a new column and assigns a 1 or 0 (True/False) value to the column. To do this, I used Panda's get_dummies() function. This has the benefit of not weighting a value improperly but does have the downside of adding more columns to the data set.


## Aggregations



