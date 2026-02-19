# Specification: RSRS Statistical Trend Following

## 1. Objective
A statistical arbitrage strategy using RSRS to identify high probability trend breakouts while differentiating between Risk On and Risk Off environments.

## 2. Parameters
* N = 18 Regression Window
* M = 600 Standardization Window
* Threshold = 0.8 Z Score Trigger

## 3. Signal Generation
    ALGORITHM CALCULATE_RSRS(Asset):
        Slope, R2 = OLS(X=Low_Prices, Y=High_Prices)
        Raw_Score = Slope * R2
        Z_Score = (Raw_Score - Mean(Raw_Score)) / Std(Raw_Score)
        
        IF Z_Score > Threshold:
            RETURN SIGNAL_BUY
        ELSE IF Z_Score < Threshold_Negative:
            RETURN SIGNAL_SELL
        ELSE:
            RETURN SIGNAL_HOLD

## 4. Trend Quality Filter
    FUNCTION CALCULATE_RANKING_SCORE(Asset):
        Slope_Close, R2_Close = OLS(Time, Log(Close_Prices))
        Gini_Coef = Gini(Daily_Returns)
        Final_Score = (Slope_Close^2) * R2_Close * (1 - Gini_Coef)
        RETURN Final_Score
