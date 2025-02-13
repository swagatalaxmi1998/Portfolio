# Comprehensive Stock Data Extraction for Meta

## Project Overview
This document provides an in-depth explanation of stock data extraction and analysis using Python. The process involves retrieving stock data using Yahoo Finance (`yfinance`) and web scraping techniques. The extracted data is processed, structured, and visualized to analyze trends in stock prices and revenue.

## Technology Used

-	`yfinance`: Library for accessing historical market data.
-	`pandas`: Data manipulation and analysis tool.
-	`BeautifulSoup`: Library for web scraping and extracting structured data from webpages.
-	`Matplotlib`: Visualization library for plotting stock trends.
  
## Analysis

### Stock Price Extraction Using `yfinance`

The yfinance library allows retrieving stock data in the form of a pandas DataFrame. The following steps were performed:

- First a ticker object was crated using `Ticker` which was used to create an object for Meta (META) stock, granting access to various stock-related functions.
- The `.history()` function was used to retrieve the historical share prices over a specific period (set to `max` for all available data). Extracted stock data was stored in a `.json` file for future reference.

#### Results

The graph is a chronological representation of important dates, likely marking significant achievements, changes, or events. The x-axis represents specific years (2002, 2004, 2006, 2008, 2009, 2012, 2014) and y-axis represents opening prices of Meta's stock over time. In this context, the years correspond to important milestones in the company's history. There is a steady growth in the opening price of META’s stocks overtime. 2012 could denote Facebook's Initial Public Offering (IPO and, 2014 may highlight the acquisition of WhatsApp.
This kind of stock graphs can be used in presentations, reports, or analyses to communicate the company's achievements and strategic developments to stakeholders, investors, or the public. 

### Web Scraping for Revenue Data

To extract revenue data, the `BeautifulSoup` library was used for web scraping, following these steps:

- A request was sent to the target URL to retrieve the webpage content while mimicking a browser.
- `BeautifulSoup` was used to structure the extracted HTML data.
- The revenue table was located and extracted from the parsed HTML.
- The extracted revenue data was converted into a pandas DataFrame with  `Date` and `Revenue` columns. Symbols like dollar signs and commas were removed, and invalid entries were eliminated.

In this project, a simple analysis was done to visualize the historical stock price and revenue for META using the `make_graph` function. The graphs are shows separately in `.png` format, [here](https://github.com/swagatalaxmi1998/Data-Analysis-Portfolio/tree/main/Portfolio%20Projects/Python/Stock_data_analysis/Plots) is the link. 

- **Historical Share Price**:
This graph shows the historical price of Meta's shares over time. The y-axis represents the price in US dollars, and the x-axis represents the date. The graph is commonly used to track the performance of a company's stock over a specific period.

- **Historical Revenue**:
This graph illustrates Meta's historical revenue over time. The y-axis represents the revenue in US dollars (in millions), and the x-axis represents the date. This graph helps in understanding the financial growth and trends of the company.

## Conclusion
This project demonstrates the capability of `yfinance` for extracting historical stock data efficiently and BeautifulSoup for scraping structured financial data. By simply using `pandas` and `Matplotlib`, the extracted data was cleaned, structured, and visualized, providing valuable insights into `Meta Platforms'` stock and revenue trends.
 
