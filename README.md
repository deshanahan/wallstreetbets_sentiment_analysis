# wallstreetbets_sentiment_analysis

# Introduction
The goal of the project is to make a user-friendly investment tool using live sentiment analysis from a Twitter stream, compare that data to data from a previous period to give investors real-time insight into a company of their choice.  

The team consists of Dylan Shanahan, Jason Mannion, and Askari Amir.  We are all interested in investing powered by data science and gaining an edge in the stock market.  

Hypothesis: We can compare live sentiment analysis to sentiment analysis from previous periods to make investment decisions.

# Similar Approaches
Below are some examples of previous research into investing sentiment analysis:

QuiverQuant has put together insights from wallstreetbets comments data including metrics such as most-mentioned stocks and a mentions vs. movement metric that plots the movement of the asset as measured by its daily high / daily low and plots it with color for sentiment and size for volume. - https://www.quiverquant.com/wallstreetbets/

The novel approach is comparing live streaming sentiment analysis data to previous sentiment analysis data on retail investors.

# Methodology
The user will enter in a stock of their choice into a convenient GUI.  The user's stock will be filtered from the previously pulled wallstreetbets comments, where sentiment scores will be determined via the Vader Lexicon in nltk.  This sentiment analysis will be the feature for the models.  The target for the regression models will be the daily closing price of the user's selected stock.  The best parameters for both the regression and classification models will be chosen through GridSearchCV.  The output of the regression program will be a bar chart displaying the models' predicted values - the latest change from the stock's daily open price.  This way, short-term traders can have some of the latest information at their fingertips to make more informed decisions.

The classification version of the program picks the best classification model for each of the two targets (Severity and Direction) from the options available and uses the mean sentiment to predict those classes and output relevant information to a scatterplot/line chart.

Additionally, these insights can be compared to the output from an interactive Facebook Prophet chart for medium to long-term investors. 

# The dataset
The data consists of over 5 million rows of comments from September 9, 2020 to September 9, 2021 pulled from r/wallstreetbets and live sentiment analysis data from Twitter.


![image](https://user-images.githubusercontent.com/62728362/140200866-52323ee4-bd5f-42bc-b61a-310c9fe4e619.png)

The wallstreetbets data will be used training data for four machine learning regression models.

Other data consists of historic and streaming data from yfinance on a stock of the user's choice.

# The models
The models used in the regression form of the program are:
1. Linear Regression
2. Random Forest
3. Bayesian Ridge
4. Gradient Boosting

The models used in the classification form of the program are:
1. Logistic Regression
2. Random Forest
3. Gaussian Naive Bayes
4. Gradient Boosting

Additionally, the program uses gives medium to long-term traders the power of Facebook Prophet's additive model, which fits time-series data with seasonality and holiday effects and typically handles outliers well. 

https://facebook.github.io/prophet/

# Output
Regression version:

![image](https://user-images.githubusercontent.com/62728362/142792249-c0599bc7-6f99-419a-882b-fbf1076e7048.png)




Classification version:
![image](https://user-images.githubusercontent.com/62728362/144310061-b7ab651c-ad97-4ac7-9eb1-bb8fe1635de9.png)


The classification version of the program classifies the severity of the stock's price into four categories based on the stock's historical performance:
1. Very High
2. High
3. Low
4. Very Low

Additionally, the direction of the stock is classified based on the positivity or negativity of the stock's performance:
1. Positive
2. Negative

The classification models appear to be more accurate than the regression models.
In the classification version, the program will output a series of scatterplot markers depending on the models' predictions and the current location of the stock price relative to the stock's open price for that day, including:
1. Pos Strong Buy
2. Pos Buy
3. Pos Weak Buy
4. Pos Stay
5. Pos Weak Sell
6. Pos Sell
7. Neg Strong Sell
8. Neg Sell
9. Neg Weak Sell
10. Neg Stay
11. Neg Weak Buy
12. Neg Buy
