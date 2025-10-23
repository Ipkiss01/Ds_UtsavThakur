# Trader Performance vs Bitcoin Fear–Greed

A data analysis project that quantifies how trader performance and activity vary with Bitcoin market sentiment using the Fear–Greed Index (0–100) and per‑trade historical data.  
All work is organized for Google Colab and follows the `ds_UtsavThakur` submission structure.

## Repository layout
ds_UtsavThakur/
├─ notebook_1.ipynb # main workflow (load, prep, analysis, figures)
├─ notebook_2.ipynb # optional experiments / robustness
├─ csv_files/ # raw + processed CSVs
├─ outputs/ # charts and visual exports
├─ ds_report.pdf # final report (exported)
└─ README.md # this file


## Data
- Fear–Greed index: `csv_files/fear_greed_index-1.csv` with columns like `timestamp`, `value` (0–100), `classification` (Extreme Fear → Extreme Greed), and `date`.
- Historical trades: `csv_files/historical_data-2.csv` with per‑trade records (e.g., side, size, fee, leverage, price, realized PnL if available).

> Ensure timestamps are parsed to UTC; both datasets are floored to daily keys and merged on `day`.

## Quick start (Colab)
1. Open `notebook_1.ipynb` in Google Colab.  
2. Set file paths to `./csv_files/...` and run all cells.  
3. Figures will be written into `./outputs/` and are referenced by the report.

## Methods
- Preprocessing: standardize column names, parse timestamps, create a daily key (`.dt.floor('D')`), and drop duplicates on day for the sentiment file.
- Aggregations (daily): 
  - Trades (count), sum/mean PnL, average leverage, total fees, buy ratio.
- Join: left merge daily trading aggregates with Fear–Greed daily record.
- Analyses:
  - Grouped comparisons of average PnL and total trades by sentiment classification.
  - Pearson correlation and regression of index `value` vs daily PnL.
  - Standardized (z‑score) overlay of PnL/activity vs Fear–Greed value.

## Reproducing figures
- Average Daily PnL by Classification 
- Total Trades by Classification 
- Overlay (z‑scores)  
- Scatter + regression 

## Interpretation guide
- Compare performance across regimes (Extreme Fear, Fear, Neutral, Greed, Extreme Greed).
- Use correlation and regression as summary measures of association; inspect confidence bands.
- Treat sentiment as a complementary signal; validate with risk controls and robustness tests.

## Extending the work
- Lag tests (e.g., T−1 sentiment), risk‑adjusted metrics (Sharpe, drawdown), outlier winsorization.
- Intraday analysis or alternative windows (e.g., weekly aggregates).

## Environment
- Python 3.x
- pandas, numpy, seaborn, matplotlib

## License and contact
- License: MIT (or as required).
- Contact: <your_email> for questions or collaboration.
