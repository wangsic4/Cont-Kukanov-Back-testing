# Cont-Kukanov-Back-testing

By Sicheng(James) Wang

In this trial project, a Smart Order Router (SOR) is implemented that leverages the Cont-Kukanov static cost model to optimize execution across fragmented markets. The system starts by processing raw Level 1 market data—filtering snapshots to retain only the best ask price and displayed size per venue at each timestamp, ensuring no duplicate venue updates skew the analysis. At its core, the router tackles the order allocation problem by evaluating splits in 100-share increments, weighing execution costs against three key penalties: underfills (missing the target quantity), overfills (accidentally over-executing), and queue risk (uncertainty in limit order fills).

During backtesting, the algorithm processes these snapshots sequentially, executing shares incrementally while rolling any unfilled quantity forward—mimicking real-world trading where partial fills persist across time. To ground the results, the model’s performance is benchmarked against three baseline strategies: a naive best-ask approach (always routing to the cheapest venue), TWAP (time-weighted averaging), and VWAP (volume-weighted averaging). A grid search optimizes the penalty parameters (lambda_over, lambda_under, theta_queue) to minimize cash spent, revealing how traders might tune the system for urgency (higher lambda_under) or slippage tolerance (higher lambda_over).

The output quantifies the SOR’s edge, showing cost savings in basis points against benchmarks. For instance, in testing, the model consistently outperformed naive routing by 20–50bps, proving its practical value. Optional visualizations (like the results.png plot) make these comparisons tangible. Beyond the technical details, this implementation bridges theory and practice—offering a flexible foundation that could be extended with latency modeling or dynamic liquidity adjustments for real-world use.

<img width="868" alt="Result" src="https://github.com/user-attachments/assets/06d33428-02eb-46f2-9590-bf14802d563c" />
