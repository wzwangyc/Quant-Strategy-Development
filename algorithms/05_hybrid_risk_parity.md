# Specification: Hybrid Risk Parity and Micro Cap

## 1. Objective
Replaces fixed ETF allocation in non alpha months with a Risk Parity model to minimize portfolio variance.

## 2. Schedule
* Alpha Mode Micro Cap: Feb, Mar, May, Jul, Aug, Sep, Oct, Nov.
* Beta Mode Risk Parity: Jan, Apr, Jun, Dec.

## 3. All Weather Risk Parity
    UNIVERSE_RP = [LowVol_50, Gold, Nasdaq, FreeCashFlow, Semiconductor]

    ALGORITHM COMPUTE_RISK_PARITY(Returns_Matrix):
        Covariance_Matrix = Cov(Returns_Matrix)
        
        DEFINE Objective_Function(Weights):
            Portfolio_Vol = Sqrt(Weights.T * Covariance_Matrix * Weights)
            Marginal_Risk_Contrib = (Covariance_Matrix * Weights) / Portfolio_Vol
            Risk_Contrib = Weights * Marginal_Risk_Contrib
            RETURN Variance(Risk_Contrib)
            
        Constraints: Sum(Weights) = 1.0, Weights >= 0
        Optimized_Weights = Minimize(Objective_Function)
        RETURN Optimized_Weights
