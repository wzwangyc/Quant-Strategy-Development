# Specification: Liquidity Adjusted Global Rotation

## 1. Objective
To capture global beta across diverse asset classes while filtering out assets with high implicit trading costs using an Illiquidity Amplification metric.

## 2. Universe Definition
The strategy rotates among the following asset classes:
* Commodities: Gold ETFs, Soybean Meal
* Equity Large Cap: CSI 300, A50
* Equity Tech: Nasdaq 100
* Smart Beta: High Dividend, Quality
* Growth: ChiNext, STAR 50
* Size: CSI 1000, CNI 2000

## 3. Core Logic

### 3.1 Liquidity Gating
    FUNCTION FILTER_LIQUIDITY(Universe):
        Valid_Pool = []
        FOR EACH Asset IN Universe:
            Daily_Illiq = Abs(Return) / Turnover_Value
            Avg_Illiq = Mean(Daily_Illiq, Window=100)
            Impact_Cost = Avg_Illiq * Estimated_Order_Size
            
            IF Impact_Cost <= 0.005:
                Valid_Pool.APPEND(Asset)
        RETURN Valid_Pool

### 3.2 Ranking and Selection
    FUNCTION SELECT_WINNERS(Valid_Pool):
        Scores = {}
        FOR EACH Asset IN Valid_Pool:
            Ann_Ret = Annualized_Return(Window=10)
            Ann_Vol = Annualized_Volatility(Window=10)
            Sharpe = Ann_Ret / Ann_Vol
            Scores[Asset] = Sharpe
            
        SORT Scores DESCENDING
        RETURN Top(N) Assets
