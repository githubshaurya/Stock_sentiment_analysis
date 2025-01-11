# Sentiment based Stock Analysis 
*Objective*
The project aims to develop a sentiment analysis 
model to predict the movement of stock prices based on 
textual data from news articles. 
Coding Languages Used: Python (Librararies Used: Numpy, 
Pandas, vaderSentiment, TextBlob, sklearn, imblearn, 
backtesting, yfinance 
) 
*Procedure*
1. News article headlines scraping using New York 
Times API key. (from 1 Jan 2023 to 10 April 2024)I have 
extracted data for Apple, Nvidia and Tesla. 
2. Stock Price Extraction(OHLC) using yfinance. 
3. Labelling: (i). Increase(if price change>0.01) 
(ii). Decrease (if price change<-0.01) else no change. 
4. Horizontally concatenate stock price and news headline 
data for the dates present in both of them. 
5. Replacing Categorical Labels(‘Increase’:1 , ‘Decrease’: -1 
and ‘no_change’:0 ) 
6.Applied stock_sentiment_analyser to headline data and got 
compound, positive, negative and neutral scores. 
7. Getting subjectivity and polarity scores for headlines using 
TextBlob library. 
8. Applying Train_Test_split to distribute all three 
dataframes(one for each company) into 80:20 to get training: 
testing data. 
9.  Applying CountVectorizer().fit_transform to headlines in 
training and CountVectorizer().transform to headlines in 
testing data. 
10. Concatenating training parts for each dataframe and then 
concatenating testing parts. 
11. Balance imbalance in Training data target column i.e. 
Label using SMOTE.  
12. Using Random Forest, SVM and Logistic Regression to 
train the model on  training data. 
13. Evaluate model using accuracy score and Classification 
report. 
14. developed an strategy use backtesting to backtest it only 
on Tesla Data. 
15. Using bt.plot() to plot three graphs:  
(i). First graph tells about the net equity I have. 
(ii). Second tells about the profit and loss. It also contains 
candlestick-patterns. 
(iii). Third graph tells about the volume traded oon each date. 
*Strategy* 
1. Calculating SMA(Simple Moving Average) :SMAs are 
used to smooth out price data and identify trends by 
averaging out short-term fluctuations. Two SMAs with 
different periods (4 and 8) are used to detect trend 
changes through crossover signals. 
2. Sentiment threshold is used to filter sentiment scores, 
ensuring that only strong sentiment signals (either 
positive or negative) trigger trades. 
3. Uses sentiment analysis scores (‘Compound’, ‘Polarity’, 
‘Subjectivity’) to decide if the market sentiment 
supports a 'long' or 'short' position. 
(i). subjectivity indicates the presence of personal views, 
opinions, or feelings. 
(ii). The polarity score measures the emotional tone, 
indicating whether the expressed sentiment is positive, 
negative, or neutral. 
(iii). Compound score combines the effects of individual 
sentiment-bearing words into a single score.It captures 
the overall sentiment in a straightforward manner. 
4. Bullish Crossover: When the shorter-period SMA (sma1) 
crosses above the longer-period SMA (sma2), it indicates 
a potential uptrend, generating a 'buy' signal. 
Bearish Crossover: When the shorter-period SMA 
(sma1) crosses below the longer-period SMA (sma2), it 
indicates a potential downtrend, generating a 'sell' 
signal. 
5.  Positive Sentiment (Long): If the subjectivity is high 
(greater than 0.5) and the compound score is positive 
(greater than 0.1), it generates a 'long' signal. 
Negative Sentiment (Short): If the subjectivity is low 
(less than 0.5) and the compound score is negative (less 
than -0.1), it generates a 'short' signal. 
6. Buy Signal: If an SMA bullish crossover occurs and the 
sentiment signal is 'long', the strategy closes any existing 
short positions and opens a long position. 
Sell Signal: If an SMA bearish crossover occurs and the 
sentiment signal is 'short', the strategy closes any 
existing long positions and opens a short position. 
No Trade: If there is no sentiment signal, the strategy           
closes any open positions and remains out of the market.

*Strategy Analysis*: 
1. The strategy has a Sharpe Ratio of approximately 0.634, 
indicating a good risk-adjusted return compared to the 
risk-free rate. 
2. Max Drawdown: The maximum drawdown experienced 
during the backtest period is around -7.178%, which 
means that strategy does not expose the portfolio to 
excessive risk. 
3. The strategy made a total of 9 trades over the 
backtesting period. This low number of trades suggests 
the strategy is relatively selective 
4. A win rate of 55.55% indicates that slightly more than 
half of the trades were successful, which is a positive 
outcome. 
5. A value above 1 indicates that the strategy is profitable, 
and a value of 1.84234 is quite good, suggesting that the 
strategy generates almost twice as much profit as it 
incurs in losses. 
Conclusion:  A high risk appetite trader will be 
disappointed by the strategy made as it has primary focus on 
preventing losses but the strategy will be highly beneficiary 
for a person who wants to lower the risk as well as to the 
beginner who wants to build the confidence in share market. 
Overall, the strategy does relatively lesser number of trades 
and also generates only mediocre returns which indicates its 
risk-free attitude. 
As most of the people in India are middle and lower-middle 
class, the strategy is highly suited for them. 
