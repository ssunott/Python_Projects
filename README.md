# Personal Stock Portfolio Management App

## Objective
A simple-to-use application that keeps track of a stock portfolio, purchase price, selling price, current stock price, and provides insights such as top-performing stock, break-even price, total return, etc. to the user.

---

## Initial Findings

- **Reliable Data Source**: While there are many APIs available to retrieve financial data, the Python library `yfinance` (Yahoo Finance) is one of the most-used and reliable sources. Its functionality is more than enough to cover the needs of this project.  
- **Ticker Validation**: It is crucial to enter the correct stock ticker or symbol. Therefore, a mechanism should be in place to validate if the user enters a valid ticker.  
- **Complexity of Performance Calculations**: Stock portfolio performance calculations can be very complicated and sophisticated. There are many ways to calculate realized profit/loss, unrealized profit/loss, and to measure performance by time-weighted vs. money-weighted metrics. For the scope of this project, a simplified set of formulas will be established to perform straightforward calculations on the stocks in the portfolio.

---

## Methodologies

### Data Collection and Storage

- **Data Volume**: Since this app targets personal use, the volume of data can be managed using a flat file (e.g., CSV). Portfolio information can be manually entered by the user via the app or the CSV can be updated directly as needed.  
- **Real-Time Stock Price and Ticker Validation**: Implemented using the Python library `yfinance`.

### Portfolio Performance Calculation and Visualization

- **Descriptive Statistics**:  
  - The app displays a summary of current stock prices, average cost, quantity, profit/loss, and returns as a chart.  
  - Calculations are done on an ad-hoc basis to ensure the most up-to-date data.  
  - Performance calculation is implemented in the function `_get_performance()`. Formulas are simplified as follows:
    - **Total Shares / Shares on hand** = Sum of all shares (positive + negative)  
    - **Total Cost** = Sum(buy_shares * buy_price) + Sum(sell_shares * sell_price)  
    - **Average Cost** = Total Cost / Total Shares  
    - **Current Value** = Total Shares * current_price  
    - **Profit (when shares == 0)** = Total selling amount - Total invested amount  
    - **Profit (when shares > 0)** = Current Value - Total Cost  
    - **Return%** = (Profit / Total Cost) * 100  

- **Visualization**:  
  - Use plots (e.g., line charts, bar charts, pie charts) to identify ranking, trends, and outliers in the data.
