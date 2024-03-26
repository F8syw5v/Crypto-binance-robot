# Crypto-binance-robot
Cryptocurrency, Binance (Binance), Bitcoin (BTC), Ethereum (ETH), Litecoin (LTC), Dogecoin (DOGE), Shiba Inu Coin (SHIB), quantitative trading system, Huobi (Huobi), OKEx, trading strategies, quantitative strategies, automated trading.

# Introduction
This is a cryptocurrency quantitative trading system that utilizes Binance's trading API.

If you don't have a Binance account yet: [Registration Page](https://www.binance.us/register) (register through the link to enjoy trading cashback promotions).

In this world, there is no guaranteed way to make money; quantitative trading strategies are just auxiliary tools.

Life and death are predestined, wealth comes from the heavens! The cryptocurrency market carries risks, so entering it requires caution!

# Dual Moving Average Strategy
Taking ETH as an example, with 5-minute candlestick data, the 5-period moving average (MA5) and the 60-period moving average (MA60) are considered:

When MA5 crosses above MA60, it's a golden cross, indicating a buy signal.
When MA5 crosses below MA60, it's a death cross, indicating a sell signal.
![image](https://user-images.githubusercontent.com/18456518/119827775-18c59400-bf2c-11eb-821b-addda37b3b4a.png)

This is a favorable scenario where you can make some profits.

<img width="1643" alt="image" src="https://user-images.githubusercontent.com/18456518/119828150-7b1e9480-bf2c-11eb-9443-d0d6c1f387ab.png">

This is a scenario characterized by volatility, where losses may occur.

Adjustments to the candlestick and moving average parameters must be made based on individual circumstances.

If you don't have a Binance account yet: [Registration Page](https://www.binance.us/register) (register through the link to enjoy trading cashback promotions).

# Why Choose Binance Exchange
Transaction fees may seem insignificant at first, but as the number of trades increases, they can become a significant expense. That's why I chose Binance, a large platform exchange with low fees.
> Huobi Fees: Maker 0.2%, Taker 0.2%
> Binance Fees: Maker 0.1%, Taker 0.1% (With BNB holdings, fees can be as low as 0.075%)
If you don't have a Binance account yet: [Registration Page](https://www.binance.us/register) (register through the link to enjoy trading cashback promotions).

# Operating Environment
Python 3

# Quick Start
1.Obtain the Binance API api_key and api_secret.
Apply for an API key at: [Binance API Management Page](https://www.binance.com/cn/usercenter/settings/api-management)

2.Register a DingTalk custom robot webhook to push trading information to a specified DingTalk group.
How to Register a DingTalk Custom Robot

3.Modify the authorization file in the app directory.
```
api_key='Your Binance key'
api_secret='Your Binance secret'
dingding_token = 'Your DingTalk group assistant token'   # Strongly recommend using
```

4.Configure trading strategy information in strategyConfig.py.
Set your configuration:
```
# Moving averages, ma_x must be greater than ma_y
ma_x = 5
ma_y = 60

# Binance
binance_market = "SPOT"  # Spot market
kLine_type = '15m'  # 15-minute candlestick type, you can set it to 5-minute candlestick: 5m; 1-hour: 1h; 1-day: 1d
```
When MA5 crosses above MA60, execute a buy order.

When MA5 crosses below MA60, execute a sell order.

You can adjust the values of ma_x and ma_y according to your preferences.

You can also adjust kLine_type to choose between 5-minute, 15-minute, 30-minute, 1-hour, or 1-day candlesticks; different candlesticks may yield different results.

5.Trading Multiple Coins Simultaneously
In robot-run.py, create multiple order manager objects:

```
# Purchase DOGE with USDT, limited to a maximum of 100 USDT
orderManager_doge = OrderManager("USDT", 100, "DOGE", binance_market)
# Purchase ETH with USDT, limited to a maximum of 100 USDT
orderManager_eth = OrderManager("USDT", 100, "ETH", binance_market)
```
Add orderManager_doge and orderManager_eth to the method executed at intervals:

```
def binance_func():
    orderManager_doge.binance_func()
    time.sleep(10)
    orderManager_eth.binance_func()
```
The program can simultaneously monitor the moving averages of DOGE and ETH and execute trades based on the strategy. You can add other coins as needed.

6.Run the Program
```
python robot-run.py
```
