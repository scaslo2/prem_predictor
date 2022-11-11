# Prem Match Predictor
Using Machine Learning, I created a model that can predict the Outcome of a Barclay's Premier League soccer (or football) match.


## Web Scraping:
Create two functions using the BeautifulSoup Python package that scrapes the web. 
1. The first webscraper creates a dataframe of historical data from every premier league game in the past five years.
2. The second webscraper gets this years schedule for every game in the premier league.

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
Aggregate and normalize the historical data and develop an offensive metric and defensive metric to better predict the outcome of a game.


## Data Preperation
Separate the team names from the numerical data. Our model cannot work on non-numerical data. We will come back and merge the team name dataframe with the model results.

## Train, Test, Split
instantiate a Random Forest Model. Split the data into a training series and a testing series. Run the training to train our model and the testing to generate accuracy score. Our accuracy score for our model comes out to, XX%.
- insert notes on why a Random Forest Model here: 
These are the top indicators of game results:
- List here.


## Use Model on Current Season
Since the historical data will have more teams than are currently in the Premier League (due to relegation of the bottom three teams every year and promotion from the top three teams of the Championship) we need to only match the teams in the current schedule dataframe.

Apply the metrics we developed to each team. 

***The caveat here is Nottingham Forest. They have not been in the Premier League since 1998. We will then have to run a separate analysis using only Premier League games played so far this season by Nottingham Forest. Then we will merge this back into our current_season dataframe.***

From here, we will use our model to predict the outcome of each game.


### Side Quest: Full Season Analysis
For fun we can predict the outcome of this years premier league season. We will use our model to predict the winner of every game. Then, we will create a function that will loop through each game's result - home win, home loss, or draw - and apply the appropriate number of points for the home team in a new column (i.e. 3 points for a home win, 0 points for a home loss, and 1 point for a home draw). Next we will sum each teams total points and order the teams by this. This will give us our season's final standings. 

