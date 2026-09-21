# S&P 500 vs Nifty 50

This project is a comparison of the S&P 500 (`^GSPC`) and the Nifty 50 (`^NSEI`) over 2020-01-01 to 2026-09-01, asking two questions: which index actually delivered more to an investor, and how closely the two markets move day to day.

## Running it

```bash
pip install yfinance pandas numpy matplotlib
python sp500_vs_nifty.py
```

Adjust `START` and `END` at the top of the script to change the window.

## Method

Daily closes for both indexes plus the USD/INR rate (`INR=X`) are pulled from Yahoo Finance via `yfinance`.

The two markets keep different holiday calendars, so only days on which both were open are kept — 1,594 of them. Without this the return series are misaligned and the correlation is meaningless.

Headline returns aren't comparable across currencies, so the Nifty is converted to dollars by dividing by USD/INR. All three series are then rebased to 100 at the start date. For co-movement, daily percentage changes are plotted against each other with a least-squares line.

## Results

| Index          | Total  | CAGR  | Ann. vol |
| -------------- | ------ | ----- | -------- |
| S&P 500        | 135.9% | 13.8% | 20.5%    |
| Nifty 50 (INR) | 96.1%  | 10.6% | 18.1%    |
| Nifty 50 (USD) | 46.0%  | 5.8%  | n/a      |

The S&P won in both currencies. In rupees it beat the Nifty by 40 percentage points; in dollars, by 90. The rupee depreciated 34.3% against the dollar over the period, and that alone accounts for the difference between the two Nifty results. The orange and green lines in the left chart are the same index; the gap between them is currency.

Daily return correlation is 0.32, with a regression slope of 0.28. The scatter is a loose cloud rather than a line. The two markets trade in non-overlapping sessions, so US news reaches the Nifty a day late and same-day moves are only weakly linked. The exception is visible in the left chart: in the March 2020 crash both fell together, with the Nifty dropping further in dollar terms because the rupee sold off at the same time.

The Nifty was the less volatile of the two in local terms, 18.1% against 20.5%.
<img width="2148" height="1330" alt="image" src="https://github.com/user-attachments/assets/139db248-9e46-4c8c-b574-8dc66a69fa36" />

## Takeaway

The S&P won outright, but currency decides by how much. The 34.3% rupee depreciation more than doubles the gap for a dollar-based investor, from 40 points to 90, which means the size of the result only has an answer once you specify whose currency the investor spends. For an Indian investor holding domestically the Nifty was the weaker but less volatile asset; for a US investor the same index was the worse trade by a wide margin.

The correlation of 0.32 says the two markets are loosely linked day to day, largely because their sessions don't overlap, which could be a genuine case for holding both. The March 2020 drawdown is a reminder that the diversification is weakest in exactly the periods it would matter most.
