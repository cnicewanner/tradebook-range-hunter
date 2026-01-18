# Trend Buddy

## Summary
An automated system for trading into existing and newly forming trends.

## Stock Selection
* Stock selection is currently done manually.
* 8 stocks are watched each day.
* Stocks are choosen by:
  * Take all stocks over 200% RVOL in the premarket.
  * Remove any stocks that have under $5 ATR.
  * Remove any stocks that have under 200k premarket volume.
  * Remove any stocks that are very wicky or have gaps in their premarket data.
  * Remove any stocks that are over $600.
  * Remove any stocks that have consumed more than 60% of their daily ATR in the premarket / after hours.
    * ATR is calculated using the difference of the high and low, compared to the DAS provided daily ATR value for the previous trading day:
      * high is defined as, the higher of the premarket high or previous day close.
      * low is defined as, the lower of the premarket low or previous day close.
  * Manually analyze each of the remaining stocks to find 8 stocks that "feel" like they are going to trend.
    * This involves looking for stocks that are setting up for a play (ABCD, breakout, trending, or at edge of range) on the daily, 60-minute, or 15-minute charts.
    * If more than 8 stocks exist, favor TSLA, PLTR, HOOD, GOOGL, AMD, NVDA, RKLB, AAPL or other stocks that I have traded regularly, verses those that I have never or rarely trade.
    * If less than 8 stocks exist, select from TSLA, PLTR, HOOD, GOOGL, AMD, NVDA, RKLB, or AAPL, to fill the remaining spots, selecting those in the best position for a potential trend play.
  * If trading live, AAPL cannot be traded until March 15, 2026 to avoid tax issues.

## Timeframe
* Only enter a trade between 9:30 EST and 15:30 EST.
* On days the market closes early, do not trade.
* Do not hold trades overnight or into the after hours.

## Entry Criteria
* Note: All candle and moving averages referenced refer to the 1-min chart values, unless otherwise noted.
* ABCD:
  * Confirmation Candle:
    * Needs to have a strength index over 0.4 (for long) or under -0.4 (for short).
    * The moving averages need to be stacked in the direction of the trade.
      * Long: Price >= 9-EMA >= 20-EMA >= 50-SMA, and Price >= 200-SMA.
      * Short: Price <= 9-EMA <= 20-EMA <= 50-SMA, and Price <= 200-SMA.
    * **Low of pullback trade**:
      * Stock state needs to be in a pullback.
      * Needs to be bouncing off of the 9-EMA, or 20-EMA, or the high (long) / low (short) of the previous range, or the high (long) / low (short) of the previous pullback.
      * The direction of the trade needs to be:
        * in alignment with the daily and hourly trend, or
        * against the daily trend and the hourly trend has not yet setup.
    * **Continuation trade**:
      * Stock state needs to be in a continuation following a pullback.
      * Needs to be one of the following:
        * Bouncing off of the 9-EMA with the EMAs stacked properly
          * Long: Price >= 9-EMA >= 20-EMA >= 50-SMA.
          * Short: Price <= 9-EMA <= 20-EMA <= 50-SMA.
        * Bouncing off of the high (long) / low (short) of the previous range.
        * Bouncing off of the high (long) / low (short) of the previous pullback.
      * The direction of the trade needs to be:
        * against the daily trend, and
        * the hourly trend has not yet setup, and
        * the hourly moving averages should not be stacked properly in either direction.
* 5-min Trend Reversal Candle:
  * Entry is at the open of the current 5-min candle, instead of the break of the confirmation candle.
  * **Long 1 (single candle)**:
    * Previous 5-min candle closed above the 9-EMA and the 20-EMA.
    * Previous 5-min candle crossed the 9-EMA and the 20-EMA.
    * High of confirmation candle is the high of the previous 5-min candle.
    * Low of confirmation candle is the low of the previous 5-min candle.
    * The daily trend needs to be:
      * Short and the hourly trend needs to be long or not yet setup, or
      * Long and the hourly trend has not yet setup.
  * **Long 2 (double candle)**:
    * Previous 5-min candle closed above the 9-EMA and the 20-EMA.
    * Previous-Previous 5-min candle crossed the 9-EMA and the 20-EMA.
    * High of confirmation candle is the high of the previous 5-min candle.
    * Low of confirmation candle is the low of the previous-previous 5-min candle.
    * The daily trend needs to be:
      * Short and the hourly trend needs to be short, or
      * Long and the hourly trend is short.
  * **Short 1 (single candle)**:
    * Previous 5-min candle closed below the 9-EMA and the 20-EMA.
    * Previous 5-min candle crossed the 9-EMA and the 20-EMA.
    * Low of confirmation candle is the low of the previous 5-min candle.
    * High of confirmation candle is the high of the previous 5-min candle.
    * The daily trend needs to be:
      * Long, or
      * Short and hourly trend is short.
  * **Short 2 (double candle)**:
    * Previous 5-min candle closed below the 9-EMA and the 20-EMA.
    * Previous-Previous 5-min candle crossed the 9-EMA and the 20-EMA.
    * Low of confirmation candle is the low of the previous 5-min candle.
    * High of confirmation candle is the high of the previous-previous 5-min candle.
    * The daily trend needs to be:
      * Long, or
      * Short and hourly trend is short or not yet setup.

### Determining Daily Trend Direction
* If the previous daily candle closed above the daily 9-EMA, it is trending long. Otherwise, the trend is trending short.

### Determining Hourly Trend Direction
* Long:
  * Current 1-min candle is above the 60-min 9-EMA, and
  * Current 1-min candle is above the 60-min 50-SMA
* Short:
  * Current 1-min candle is below the 60-min 9-EMA, and
  * Current 1-min candle is below the 60-min 50-SMA
* No Trend Formed:
  * Trend is neither long nor short

### Identifying a Bounce from a Level / Moving Average
* A candle is considered to have bounced from a level (level or moving average) if:
  * Long:
    * The candle closes above the level.
    * The candle closes more than 75% of the 1-min ATR above the level.
    * The candle opens above the level, or no more than 10% of the 1-min ATR below the level.
    * The low of the candle is no more than 35% of the 1-min ATR above or below the level.
  * Short:
    * The candle closes below the level.
    * The candle closes more than 75% of the 1-min ATR below the level.
    * The candle opens below the level, or no more than 10% of the 1-min ATR above the level.
    * The high of the candle is no more than 35% of the 1-min ATR above or below the level.

### Calculating Candle Strength Index
* The strength index of a candle is a value between -1 and 1.
* The value is calculated by taking the sum of the body's strength, the upper wick's strength, and the lower wick's strength, and then dividing that sum by the size of the candle.
  * Body Strength is calculated by subtracting the open of the candle from the close of the candle (close - open).
  * Upper Wick Strength is calculated by subtracting the high of the candle from the high of the candle body (highBody - high).
  * Lower Wick Strength is calculated by subtracting the low of the candle from the low of the candle body (bodyLow - low).
  * Size is calculated by subtracting the low of the candle from the high of the candle (high - low).

### Identifying a Stock's State
* We can track a stock's state in any timeframe, following the same rules.
* If we don't know the stock's state, we look for an initial range or trend, by looping through the previous 150 candles (from the oldest to the newest), tracking the state of the stock:
  * When starting:
    * If the moving averages are stacked, we assume we have a trending moving in the direction that the averages are stacked.
      * Stacked averages means, for long the price >= 9-EMA >= 20-EMA => 50-SMA, for short price <= 9-EMA <= 20-EMA <= 50-SMA.
    * If the moving averages are not stacked, we start tracking the local high and low of the candles, waiting for a trending state to be reached.
      * If we don't reach a trend state before the 150 candles are exaushted then we use the calculated low and high as the starting range.
  * Once we have a range or a trend, we continue to walk through the remaining candles to tracking the stock's state.
* When tracking a stock's state:
  * If the current state is in a trend:
    * If the stock is trending, we continue to watch the stock until we have a pullback.
    * Once we have a pullback, we track the pullback until it starts to continue the trend.
    * If the pullback fails to continue the trend (double tops / bottoms), we mark the stock as being range bound.
    * If the pullback falls back into a previous range/pullback area, we mark the stock as having a fake breakout and mark the stock as bing in a range (using the previous range/pullback area as the range).
    * If the stock continues the trend, we mark the stock as trending and wait for another pullback.
    * If the pullback closes beyond (long below, short above) the 50-SMA we reset the trend and mark it as going in the opposite direction of the current trend.
  * If the current state is in a range, we wait for the stock to break either side of the range before marking the stock as trending.

#### Notes on Identifying State Changes
  * A pullback:
    * In a long trend: the current candle's low is lower than the previous candle's low.
    * In a short trend: the current candle's high is higher than the previous candle's high.
  * Starts to continue the trend:
    * In a pullback on a long trend: the current candle's high is higher than the previous candle's high.
    * In a pullback on a short trend: the current candle's low is lower than the previous candle's low.
  * A double top / bottom:
    * A second pullback is formed before the peak of the original pullback is broken.

#### Special State notes
  * For a pullback to be a valid pullback where we can play the continuation, it must have:
    * Involved more than 4 candles, or
    * Been at least 1.5 times the current timeframe's ATR, or
    * Been at least 20% of the current trend leg.
  * We can also play breakouts from actual levels, which can be formed in a pullback when the price crosses the 20-EMA.
  * If in a pullback the price crosses the 50-SMA, we have a trend reversal and we have to wait for the price to pullback before making any trades in the trend.

## Exit Criteria
* A trade is closed when:
  * The stop order is triggered, or
  * A 5-min candle closes beyond the 9-EMA.
    * Beyond means, for longs below the 9-EMA, for shorts above the 9-EMA.

## Trade Management Rules
* The initial risk for a trade is $15.
* Enter at the break of the confirmation candle.
* Stop loss is placed at the far end of the confirmation candle.
* Add at each 1/3 R interval, with a maximum of 6 adds.
  * Each add doubles the current position.
* If a trade is open for a given stock, do not enter a new trade.
  * However, if the potential setup is in the same direction as the existing trade, and if we have not reached 6 adds, the new setup can be used as a place to add into the existing trade.
* All orders are performed using market orders, using the DAS/IBKR SMART routes, to ensure fills happen as quickly as possible.
* If an order is not filled (for any reason) within 60 seconds, the order should be canceled.
* Any positions open at 3:59pm EST are closed to ensure no trades are held overnight.
* All stops are placed using DAS stop market orders.

## Notes


## Examples
* [TSLA  (2025-10-23) -  2 Trades](./examples/trend-buddy-tsla-2025-10-23.md)
* [AVGO  (2025-11-04) -  6 Trades](./examples/trend-buddy-avgo-2025-11-04.md)
* [GOOGL (2025-11-05) - 13 Trades](./examples/trend-buddy-googl-2025-11-05.md)
* [MU    (2025-11-06) - 12 Trades](./examples/trend-buddy-mu-2025-11-06.md)
* [GOOGL (2025-11-21) -  5 Trades](./examples/trend-buddy-googl-2025-11-21.md)

## Manual Trade Examples and Strucutre Notes
* [Manual Trades](./manual-trades/README.md)
