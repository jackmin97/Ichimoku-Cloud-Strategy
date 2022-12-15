# Ichimoku-Cloud-Strategy
In this notebook, we will create a crypto strategy using Ichimoku Cloud. The strategy works as follows:

### 1. Fetch the daily data of Bitcoin.
Fetch the Bitcoin data from 'BTC-USD.csv' using pandas read_csv function.

### 2. Compute the Ichimoku charts.
The Ichimoku Cloud, also known as Ichimoku Kino Hyo is a technical indicator, which consists of five plots and a cloud. The default parameters of Ichimoku Cloud are 9, 26, 52, 26.
Conversion line periods- 9
Base line periods- 26
Leading Span periods- 52
displacement- 26
These parameters are configurable based on the preferences of the trader and the asset class. For cryptocurrency pairs, we adjust the parameters to 20, 60, 120, 30 as the crypto market is open 24/7 and more volatile than other assets so to capture the bigger movements we almost doubled the parameter values.

###### 2.1 Tenkan-sen (Conversion Line): (20-period high + 20-period low)/2

###### 2.2 Kijun-sen (Base Line): (60-period high + 60-period low)/2

###### 2.3 Senkou Span A (Leading Span A): (Conversion Line + Base Line)/2

###### 2.4 Senkou Span B (Leading Span B): (120-period high + 120-period low)/2

###### 2.5 Chikou Span (Lagging Span): Close plotted 30 days in the past

###### 2.6 A cloud which is the area between Senkou Span A and Senkou Span B.
The Cloud is the most prominent feature of the Ichimoku Cloud plots. The Leading Span A and Leading Span B form the Cloud. As you can see in the below chart, the prices are above, below or in the cloud. The trend is up when prices are above the cloud, down when prices are below the cloud and flat when prices are in the cloud.

# 3. Trading signals

##### 3.1 Entry signal
We buy the Bitcoin:
1) When prices are above the cloud and leading Span A (senkou_span_A) is rising above the leading span B (senkou_span_B).
2) Conversion Line (tenkan_sen) moves above Base Line (kijun_sen)

##### 3.2 Exit signal
1) When prices are below the cloud and leading Span A (senkou_span_A) falls below the leading span B (senkou_span_B).
2) Conversion Line (tenkan_sen) moves below Base Line (kijun_sen)

# 4. Strategy return
The strategy returns are computed by multiplying the daily_returns with the trading signal of the previous day, assuming that the corresponding execution happens at the close of the current day.

The strategy returns are approximately 6 times from 17-September-2014 to 15-December-2022
