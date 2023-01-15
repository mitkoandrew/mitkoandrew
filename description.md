# Structure and principles of work

## 1. Input Data

The list of futures for the forecast is loaded from the server of Moscow Exchange (MOEX):
http://iss.moex.com/iss/engines/futures/markets/forts/securities.xml

To exclude the least traded futures, a condition is added:

'PREVOPENPOSITION > 50000'

this condition is necessary in order to avoid slippage (they have a minimum difference between bid / ask prices)

For every ticker in the list above, the data for prediction is downloaded from

"http://iss.moex.com/iss/history/engines/futures/markets/forts/boards/RFUD/securities/" + ticker + ".xml?from=" + init_date_str + "&till=" + cur_date_str;

After parsing xml data, the following values are used:

"CLOSE" - closing (last) price of the trading day;
"SECID" - futures code;
"TRADEDATE" - trade date;
"LOW" - minimum price of the trading day;
"HIGH" - maximum price of the trading day;

In the automatic trading system (written on Python), the data for forecast is loaded directly from MetaTrader

## 2. Forecast

The forecast is formed on the historical data obtained at the step 1. The result of the forecast is the construction of a trend for the future period. The choice of a specific forecast algorithm depends on the initial data

## 3. Operation

There are 3 types of the forecast result:

1. Up-Trend => Operation "BUY"
2. Down-Trend => Operation "SELL"
3. No Trend => No operation ("NONE")

## 4. Sending orders

In the automatic trading system (written on Python), the orders are sent automatically into the MetaTrader. All required parameters are included. Additionally,
two orders (Stop-Loss and Take-Profit) are sent within the main order.

## 5. Saving 

All operations (step 3) per day are serialized and stored in an archive file (.xml). This archive can be uploaded on the step 6 for analysis.

## 6. Analysis

The separate block is used for uploading the archive of the past operaions, calculating financial results for futures and visualizing the results.
