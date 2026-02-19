# Specification: Seasonal Rotation and Micro Cap Alpha

## 1. Objective
To exploit calendar effects in global assets and the size premium in the A share market.

## 2. Temporal Allocation
    CONSTANTS:
        MONTHS_TECH = [June]
        MONTHS_SAFE = [January, April, December]
        MONTHS_ALPHA = [February, March, May, July, August, September, October, November]

    FUNCTION GET_TARGET_ASSET(Current_Month):
        IF Current_Month IN MONTHS_TECH:
            RETURN Nasdaq_100_ETF
        ELSE IF Current_Month IN MONTHS_SAFE:
            RETURN Gold_ETF
        ELSE:
            RETURN Micro_Cap_Strategy

## 3. Micro Cap Factor Logic
    FUNCTION SELECT_MICRO_CAPS():
        Universe = All A Share Stocks
        Sorted_List = Sort Universe by Total_Market_Cap Ascending
        Candidates = Top 100 Smallest Caps
        
        Valid_List = []
        FOR Stock IN Candidates:
            IF Stock is NOT ST OR Suspended AND Stock.Price > 1.0 AND Stock.Price < 15.0:
                Valid_List.APPEND(Stock)
                
        RETURN Top 10 from Valid_List
