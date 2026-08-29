# Customer Shopping & Sales Analytics

A Python project for analyzing customer shopping transactions: cleaning messy data, breaking down sales by customer, product, city, membership tier, and payment method, and building out visualizations and correlation checks. Built with Pandas, NumPy, Matplotlib, and Seaborn.

## What's in here

- `generate_dataset.py` — creates `raw_customer_sales.csv`, a synthetic but realistic transaction log with the usual data problems baked in: missing values, duplicate rows, invalid ages, negative prices, discounts outside 0–100%, and ratings outside the 1–5 scale.
- `analysis.py` — the full pipeline. Loads the raw CSV, cleans it, runs every analysis section, generates the charts, and writes out the final files.
- `customer_shopping_analytics.ipynb` — the same pipeline as a Jupyter notebook, split into cells by section, already run once so you can see the output without executing anything.
- `raw_customer_sales.csv` — the input data (dirty, on purpose).
- `analyzed_customer_sales.csv` — the cleaned output, with a few extra columns added: Gross Sales, Discount Amount, Net Sales, Year, Month, Day of Week, and Customer Segment.
- `charts/` — eleven PNGs covering category sales, revenue by city, monthly trends, age and rating distributions, payment method breakdown, top products, customer segments, and a correlation heatmap.
- `summary_report.txt` — a short text summary with the headline numbers (total revenue, best category, top city, and so on).

## Setup

You'll need Python 3.9 or newer, plus:

```
pip install pandas numpy matplotlib seaborn
```

## Running it

If you're starting from scratch and want fresh synthetic data:

```
python3 generate_dataset.py
python3 analysis.py
```

If you already have `raw_customer_sales.csv` sitting in the folder, you can skip straight to:

```
python3 analysis.py
```

Prefer notebooks? Open `customer_shopping_analytics.ipynb` in Jupyter or VS Code and run the cells top to bottom.

## Dataset columns

Transaction ID, Customer ID, Customer Name, Age, Gender, City, Product Name, Category, Quantity, Unit Price, Discount (%), Total Amount, Purchase Date, Payment Method, Customer Rating, Order Status, Delivery Days, Membership Type.

## What the analysis covers

The script works through eleven sections in order: data cleaning, customer behavior, product and category performance, sales and revenue math (gross sales, discounts, net sales), city-level breakdowns, membership tiers, payment methods, delivery and order status, month-over-month and day-of-week trends, a set of filtered views (big spenders, frequent buyers, high discounts, and so on), and a spending-based customer segmentation into four tiers. After that comes the chart generation and a block of statistical checks, including a correlation heatmap.

## Using your own data

Swap in your own transaction export as long as the column names match the list above, then run `analysis.py` again. Everything downstream, cleaning, grouping, charts, and the summary report, will pick up your real numbers instead of the synthetic ones.

## A note on the sample data

The raw CSV that ships with this project is generated, not real customer data. It exists so the cleaning steps (handling missing values, catching invalid ages or ratings, removing duplicates) actually have something to fix, and so the analysis code can be tested end to end before you point it at your own file.
