Here are the results of the FuturePricePrediction algorithm on some liquid stocks/futures.
I made a comparative analysis of the FuturePricePrediction algorithm (FPP) with two trading strategies: 
naive (Buy&Hold) and more complex (creating forecast using ARIMA https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average)

Trade period = 200 days. Quantity per trade = 1

1. TSLA (Tesla, Inc)
Trade period = last 200 days (116 trading days). Quantity per trade = 1. Amount of deals (using FPP): 66

![image](https://user-images.githubusercontent.com/41163875/178639027-72025d6b-01d9-4d62-9aad-571751b77039.png)

Method	  |   profit/loss
__________|_______________
Buy&Hold  |   -226,97
ARIMA     |   254,11
FPP       |   595,18

2. 
