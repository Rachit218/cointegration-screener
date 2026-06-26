# Quantitative Statistical Arbitrage: Cointegration Screener


## The Mathematics of Cointegration

This tool strictly evaluates **Cointegration**—identifying when a linear combination of two non-stationary time series results in a strictly stationary series.

### 1. Optimal Hedge Ratio (OLS Regression)
To construct the spread, we first determine the optimal hedge ratio ($\beta$) using Ordinary Least Squares (OLS) regression to minimize the variance of the spread:
$$Spread_t = Price_{A,t} - (\beta \times Price_{B,t})$$

### 2. Augmented Dickey-Fuller (ADF) Test
Once the spread is constructed, we must prove it is stationary rather than a random walk. The tool applies the Augmented Dickey-Fuller test to check for the presence of a unit root:
* **Null Hypothesis ($H_0$):** The spread has a unit root (it is non-stationary / random walk).
* **Alternative Hypothesis ($H_1$):** The spread has no unit root (it is strictly stationary).

If the resulting $p\text{-value}$ is strictly $< 0.05$, we reject the null hypothesis. The pair is mathematically tethered, and the spread is stationary.

---

## Technical Architecture
* **Data Ingestion:** Automated fetching of daily historical adjusted close prices via `yfinance`.
* **Statistical Backend:** Calculates OLS parameters and conducts the ADF hypothesis testing using `statsmodels`.
* **Interactive Frontend:** Built with `streamlit`.

---

## Quick Start & Usage

**1. Clone the repository and navigate to the directory:**
git clone [https://github.com/YourUsername/cointegration-screener.git](https://github.com/YourUsername/cointegration-screener.git)
cd cointegration-screener

**2. Install the required dependencies:**
pip install pandas yfinance statsmodels streamlit

**3. Launch the Dashboard:**
streamlit run app.py
