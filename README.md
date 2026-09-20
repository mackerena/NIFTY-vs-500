# S&P 500 vs Nifty 50

A comparison of the S&P 500 (^GSPC) and the Nifty 50 (^NSEI) over 2020-01-01 to 2025-01-01, asking two questions: which index actually delivered more to an investor, and how closely the two markets move day to day.

Running it
bash
pip install yfinance pandas numpy matplotlib
python sp500_vs_nifty.py

Adjust START and END at the top of the script to change the window.

**Method**

Daily closes for both indexes plus the USD/INR rate (INR=X) are pulled from Yahoo Finance via yfinance.

The two markets keep different holiday calendars, so only days on which both were open are kept - 1,199 of them. Without this the return series are misaligned and the correlation is meaningless.

Headline returns aren't comparable across currencies, so the Nifty is converted to dollars by dividing by USD/INR. All three series are then rebased to 100 at the start date. For co-movement, daily percentage changes are plotted against each other with a least-squares line.

**Results**

	Total	CAGR	Ann. vol
S&P 500	80.5%	13.2%	21.5%
Nifty 50 (INR)	92.5%	14.8%	19.4%
Nifty 50 (USD)	59.4%	10.3%	—

In rupees the Nifty won by 12 percentage points. In dollars it lost by 21. The rupee depreciated 20.8% against the dollar over the period, and that alone accounts for the reversal. The orange and green lines in the left chart are the same index; the gap between them is currency.

Daily return correlation is 0.35, with a regression slope of 0.31. The scatter is a loose cloud rather than a line. The two markets trade in non-overlapping sessions, so US news reaches the Nifty a day late and same-day moves are only weakly linked. The exception is visible in the left chart: in the March 2020 crash both fell together, with the Nifty dropping further in dollar terms because the rupee sold off at the same time.

The Nifty was also the less volatile of the two in local terms, 19.4% against 21.5%.

**Takeaway**

Neither index won outright. The entire difference between the two results is the 20.8% rupee depreciation, which means the question only has an answer once you specify whose currency the investor spends. For an Indian investor holding domestically the Nifty was the better asset and the less volatile one; for a US investor the same index was the worse trade by a wide margin.

The correlation of 0.35 says the two markets are loosely linked day to day, largely because their sessions don't overlap, which could make for a genuine case for holding both. The March 2020 drawdown is a reminder that the diversification is weakest in exactly the periods it would matter most.
