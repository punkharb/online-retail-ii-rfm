# Online Retail II — Customer Segmentation with RFM

I used two years of online retail transactions to answer a simple question: **which customers buy recently, often, and spend more?** This is a rule-based RFM analysis, not a trained prediction model.

## What I did

- Combined the two Excel sheets without counting their overlapping December 2010 records twice.
- Kept the raw data, then made a purchase-only table for customer analysis. I excluded rows without a customer ID, cancelled/returned transactions, non-positive quantities or prices, and exact duplicate rows.
- Used transactions before **1 September 2011** to calculate Recency, Frequency, and Monetary value for each customer.
- Scored each RFM measure from 1 to 5 and assigned clear, rule-based customer segments.
- Compared each segment's share of customers with its share of positive purchase value.

## Main result

The high-value segment contains **1,225 of 5,249 customers (23.3%)** and accounts for **70.6% of positive purchase value** in the analysis period. The at-risk segment contains **568 customers** who bought several times but had not purchased recently as of 1 September 2011.

This is descriptive, not a measured campaign outcome. The high-value group is partly defined using spending, so its large purchase-value share is not an independent discovery. Returns and cancellations are excluded, so purchase value here is **not net revenue**.

## Notebook

Open [online-retail-ii-rfm.ipynb](online-retail-ii-rfm.ipynb). It includes the checks, code, output tables, chart, and short explanations of why each step was done.

To rerun it on Kaggle, attach the [Online Retail II dataset](https://archive.ics.uci.edu/dataset/502/online+retail+ii) and update the file path in the first code cell if your Kaggle input path differs. The notebook expects an Excel file with the `Year 2009-2010` and `Year 2010-2011` sheets. The dataset itself is not stored in this repository.

The notebook sets aside later transactions as `future_raw`, but does **not** use them to evaluate the segments. I have not claimed a prediction or validation score.

## Tools and limits

Python, pandas, NumPy, and Matplotlib. Exact duplicate rows were removed as an assumption; some could be genuine identical line items. Customers without IDs cannot be included in customer-level RFM.
