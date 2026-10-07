# Ecommerce Sales Analysis (Task 1)

Analysis of the UCI Online Retail dataset (UK gift retailer, 1 Dec 2010 to 9 Dec 2011). It cleans the raw data and answers three questions, with charts, uncertainty and caveats. Everything is in `notebook/01_analysis.ipynb`.

## Questions
1. Which products and countries drive revenue, and how concentrated is it?
2. Is the Q4 spike seasonality or growth?
3. How much revenue comes from repeat vs one-time customers?

## Setup
```
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
```
1. Download "Online Retail" from https://archive.ics.uci.edu/dataset/352/online+retail and unzip it.
2. Put the file in `data/raw/` and name it `online retail.xlsx`.
3. Open `notebook/01_analysis.ipynb`, select the `venv` kernel and run all cells. Loading the Excel file takes about a minute.

## Key decisions
- Removed duplicates, cancellations (InvoiceNo starting with C), quantity or price <= 0, and non-product codes. The notebook logs how many rows each step removed.
- Removed two bulk orders (74k and 81k units) that were cancelled the same day; they inflated product revenue.
- Kept rows with no CustomerID for Questions 1 and 2; excluded them from Question 3 (25% of rows).
- Uncertainty is shown as 95% bootstrap intervals.
- December 2011 is a partial month (data ends 9 Dec) and is greyed out.

## Findings
- Top 20% of products = 78.3% of revenue (95% CI 77.6-78.7%); UK = 84.8% of revenue.
- Sep to Nov = 37.5% of 12-month revenue; 1-9 Dec 2011 is 9.3% above 2010, a rough signal only.
- Repeat customers = 65.3% of customers and 93.5% of revenue (95% CI 92.5-94.5%).

## Limits
One year of data, one UK retailer, many wholesale customers, and 25% of rows without a customer ID.

## Related
Dashboard (Task 2): https://github.com/varshithavarshithac345-byte/Ecommerce_Sales_Project