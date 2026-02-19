# 📘 Quant-Strategy-Development

[![Documentation](https://img.shields.io/badge/Docs-100%25-blue)](https://github.com/)
[![Status](https://img.shields.io/badge/Status-Validated-brightgreen)](https://github.com/)
[![License](https://img.shields.io/badge/License-MIT-grey)](LICENSE)

## 📖 Overview

**Quant-Strategy-Development** is a collection of algorithmic specifications and logic designs for quantitative trading strategies. Researched and developed by **Yucheng Wang**, this repository focuses on mathematical models, signal generation logic, and execution rules.

These algorithms serve as a robust blueprint for implementation and have been strictly backtested and verified for live market effectiveness on quantitative platforms such as **Supermind** and **JoinQuant**.

**Note:** This repository contains algorithmic pseudocode and logic flow documentation only. No executable source code is provided to protect proprietary intellectual property.

## 🧠 Algorithm Matrix

| ID | Strategy Name | Type | Core Hypothesis | Specification |
|:---|:---|:---|:---|:---|
| **01** | **Liquidity Enhanced Rotation** | Global Macro | Illiquidity premium & Momentum | [View Spec](algorithms/01_liquidity_rotation.md) |
| **02** | **RSRS Trend Arbitrage** | Stat Arb | Regression slope strength vs Mean reversion | [View Spec](algorithms/02_rsrs_trend_arbitrage.md) |
| **03** | **Regime Switching Alpha** | Adaptive | Sharpe based regime detection | [View Spec](algorithms/03_regime_switching_framework.md) |
| **04** | **Seasonal Micro Cap** | Factor Calendar | Calendar anomalies & Size factor | [View Spec](algorithms/04_seasonal_microcap_alpha.md) |
| **05** | **Hybrid Risk Parity** | Asset Alloc | Convex optimization (ERC) | [View Spec](algorithms/05_hybrid_risk_parity.md) |

## 📝 Notation Standards

The pseudocode follows a standard institutional format:
* **Universe**: Asset selection pool.
* **Signal**: Mathematical formula for entry and exit.
* **Execution**: Rebalancing and portfolio weighting rules.

***
*Researched and Maintained by **Yucheng Wang***
