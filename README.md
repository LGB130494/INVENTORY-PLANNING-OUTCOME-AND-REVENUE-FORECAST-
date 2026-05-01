🚀 From Flat Lines to Accurate Forecasts — A Time Series Journey

I recently completed an end-to-end forecasting project on 5 years of daily revenue data (Jan 2018 – Nov 2022), and the results taught me more about demand planning than any textbook ever could.

Here's the full story 👇

📊 THE DATA
1,795 days of revenue — with massive annual spikes reaching 5–7x normal volume. Two business levers sat alongside it: discount_rate and coupon_rate.

Before building any model, I asked: how does this data actually behave?
✅ Strong upward trend (2018–2021), then a plateau in 2022
✅ One massive seasonal spike every year — 2x to 3x the trend level
✅ Clear weekly cycles confirmed via ACF/PACF
✅ Non-stationary raw data → required first differencing (d=1)

🔵 MODEL 1 — ARIMA(3,1,1) → MAPE: 24.18%
The baseline. It captured average revenue levels but produced a completely flat forecast — missing the November spike entirely. In supply chain terms: guaranteed stockouts.

🟡 MODEL 2 — SARIMA(3,1,1)(2,0,1,7) → MAPE: 25.89%
Added weekly seasonality (s=7). Statistically significant — but MAPE actually got worse. Why? The dominant issue was the annual peak, not the weekly cycle. A model looking 7 days back cannot anticipate a once-a-year event.

🟢 MODEL 3 — SARIMAX + discount_rate + coupon_rate → MAPE: 21.71%
The breakthrough. Adding external variables proved mathematically that:
• Every 1% increase in discount → ₹4,03,000 more revenue
• Every 1% increase in coupon rate → ₹9,22,900 more revenue
The forecast finally "jumped" in November. Promotions explain the spikes — not randomness.

🏆 AFTER TUNING (40 models × 5 CV folds)
Best model: SARIMAX(1,1,0)(2,0,1,7)
Cross-validated avg MAPE: 18% | RMSE: ₹4.35M

📦 INVENTORY PLANNING OUTCOME
The 30-day December 2022 forecast, powered by the planned promotional calendar:
✔ Safety stock = 20% buffer above forecast (covers MAPE)
✔ 3x warehouse capacity pre-positioned for annual peak
✔ Weekly replenishment aligned to day-of-week demand cycle
✔ Emergency protocol if actuals exceed forecast by >30% for 3 days

💡 KEY LESSON
Revenue spikes are NOT random. They are caused by planned promotions. Feed your forecasting model your marketing calendar — and it will tell you exactly how much stock to hold.

Tech Stack: Python · statsmodels · scikit-learn · SARIMAX · TimeSeriesSplit · ParameterGrid

#SupplyChain #DemandPlanning #TimeSeries #ARIMA #SARIMA #SARIMAX #DataScience #InventoryPlanning #Python #Forecasting #Analytics 
