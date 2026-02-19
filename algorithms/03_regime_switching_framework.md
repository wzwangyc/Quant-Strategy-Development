# Specification: Multi Factor Regime Switching

## 1. Objective
To dynamically switch between Aggressive, Defensive, and Safe Haven modes based on macroscopic market efficiency.

## 2. Regime Identification
    FUNCTION DETERMINE_REGIME():
        Calculate Sharpe Ratio for I_growth, I_value, I_rf
        Score = Sign(S) * Log(Abs(S) + 1)
        Best_Asset = ArgMax(Scores)
        
        CASE Best_Asset OF:
            I_rf: MODE GLOBAL_HEDGE
            I_growth: MODE STOCK_PICKING_GROWTH
            I_value: MODE STOCK_PICKING_VALUE
            ALL_NEGATIVE: MODE CASH

## 3. Alpha Selection Engine
    FUNCTION SELECT_ALPHA_STOCKS(Index_Constituents):
        EXCLUDE Banks, ST Stocks, New Listings
        REQUIRE Avg_Turnover > Threshold
        REQUIRE Price > 1.0 AND MarketCap_10B_to_200B AND Turnover_Rate < 0.05
        
        SORT Candidates BY Avg_High_Price ASCENDING
        RETURN Top_10_Candidates
