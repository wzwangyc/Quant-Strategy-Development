# 🏗️ Quant-Strategy-Development

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/)
[![Status](https://img.shields.io/badge/Status-Active_Development-brightgreen)](https://github.com/)
[![License](https://img.shields.io/badge/License-MIT-grey)](LICENSE)

## 📖 Overview

**Quant-Strategy-Development** is a comprehensive repository dedicated to the research, development, and backtesting of quantitative trading algorithms. This project focuses on multi-asset rotation, statistical arbitrage, and factor-based equity selection within the A-share and ETF markets.

The architecture emphasizes **robustness**, **regime adaptation**, and **risk management** over pure curve-fitting.

## 🚀 Strategy Matrix

| ID | Strategy Name | Type | Core Logic | Logic Design |
|:--:|:---|:---|:---|:---:|
| **01** | **Liquidity-Enhanced Rotation** | Global Rotation | Illiquidity amplification filter + Sharpe ranking | [View Design](logic_design/01_logic_liquidity.md) |
| **02** | **RSRS Trend Following** | Stat-Arb | RSRS slope + Gini coefficient weighting | [View Design](logic_design/02_logic_rsrs.md) |
| **03** | **Regime Switching Alpha** | Adaptive | Sharpe-based regime detection (Cash/Hedge/Growth) | [View Design](logic_design/03_logic_regime.md) |
| **04** | **Seasonal Micro-Cap** | Calendar/Factor | Fixed seasonality (Tech/Gold) + Small-cap factor | [View Design](logic_design/04_logic_seasonal.md) |
| **05** | **Hybrid Risk Parity** | Asset Alloc | Convex optimization (ERC) + Seasonal timing | [View Design](logic_design/05_logic_hybrid.md) |

## 🛠 Directory Structure

- `strategies/`: Executable Python scripts compatible with Quant/Backtest frameworks (e.g., JoinQuant/Supermind).
- `logic_design/`: High-level algorithmic pseudocode and logic flow documentation.

## ⚙️ Dependencies

- `pandas`
- `numpy`
- `scipy`
- `datetime`

## ⚠️ Disclaimer

This repository is for **research and educational purposes only**. Quantitative trading involves substantial financial risk. 

---
*Copyright © 2025 Quant-Strategy-Development Team*
