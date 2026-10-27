# RFM Customer Segmentation | Online Retail Analytics

Customer analytics project using **Recency, Frequency, and Monetary (RFM)** analysis to segment customers, explore historical purchasing patterns, and propose actionable marketing strategies.

## Project highlights

- **541,909** raw transaction lines from the Online Retail dataset.
- **397,884** cleaned positive-sales transaction lines used for the analysis.
- **4,338** identifiable customers included in the final RFM profiles.
- **8** interpretable customer segments.
- **Champions:** 795 customers (18.33%) generated **61.63%** of historical positive sales value.
- **Hibernating:** 1,206 customers (27.80%) generated **4.45%** of historical positive sales value.

## Business problem

Retail businesses need to distinguish their most valuable customers from new, inactive, and potentially disengaging customers. RFM analysis provides a transparent way to group customers based on observed transaction behavior and prioritize marketing experiments.

## Dataset

Source: [Online Retail Customer Clustering — Kaggle](https://www.kaggle.com/datasets/hellbuoy/online-retail-customer-clustering)

Relevant fields: `InvoiceNo`, `StockCode`, `Description`, `Quantity`, `InvoiceDate`, `UnitPrice`, `CustomerID`, and `Country`.

**Period:** December 1, 2010 – December 9, 2011.

The raw dataset is **not included** in this repository. Download it from Kaggle and update the data path in the notebook if needed.

## Methodology

1. **Data audit:** inspect missing customer identifiers, invalid quantities/prices, cancellations, and transaction dates.
2. **Cleaning:** retain identifiable customers and valid positive sales; exclude cancelled invoices and returns for this positive-sales RFM analysis.
3. **Exploratory analysis:** examine customer spending, invoice values, geography, and monthly sales trends.
4. **RFM feature engineering:** aggregate transactions to the customer level.
   - **Recency:** days since the customer's latest purchase, relative to the analysis reference date. Lower is better.
   - **Frequency:** number of distinct purchase invoices. Higher is better.
   - **Monetary:** sum of positive transaction value (`Quantity × UnitPrice`). Higher is better.
5. **RFM scoring:** assign 1–5 scores, with higher scores reflecting more desirable behavior; use tie-aware frequency scoring.
6. **Segmentation:** assign eight descriptive groups based on RFM scores.
7. **Interpretation:** compare customer share, revenue share, standardized RFM profiles, and recency versus monetary value.

## Results

| Segment | Customers | Customer share | Historical revenue share |
|---|---:|---:|---:|
| Champions | 795 | 18.33% | 61.63% |
| Potential Loyalists | 693 | 15.98% | 9.88% |
| At Risk | 417 | 9.61% | 7.77% |
| Loyal Customers | 216 | 4.98% | 6.87% |
| Need Attention | 684 | 15.77% | 5.87% |
| Hibernating | 1,206 | 27.80% | 4.45% |
| Can't Lose Them | 85 | 1.96% | 2.59% |
| New Customers | 242 | 5.58% | 0.95% |

The revenue shares describe **historical positive sales**, not forecasted revenue or marketing uplift.

## Business recommendations

- **Champions:** test exclusive loyalty benefits and personalized product recommendations to support retention.
- **Potential Loyalists:** encourage repeat purchases through targeted offers and post-purchase engagement.
- **At Risk / Can't Lose Them:** pilot personalized win-back campaigns and measure incremental response.
- **Hibernating:** use low-cost reactivation tests rather than blanket discounting.
- **New Customers:** encourage second purchases and build early engagement.

## Repository structure

```text
RFM-Customer-Segmentation/
├── README.md
├── requirements.txt
├── .gitignore
├── RFM_Customer_Segmentation.ipynb   # Add your completed notebook
├── rfm_customer_segments.csv         # Exported by your notebook

```

The notebook and output CSV should be added from the **completed analysis** before publishing; they are not included in this starter package.

## Run locally

```bash
python -m venv .venv
# Windows PowerShell:
.venv\Scripts\Activate.ps1
pip install -r requirements.txt
jupyter notebook
```

Open the completed notebook in `notebooks/`, download the original dataset from Kaggle, update its input path, and run the cells in order.

## Limitations

- Historical data from 2010–2011 may not reflect current retail behavior.
- Missing customer IDs prevent attribution of some sales to individual customers.
- Excluding returns means Monetary measures positive purchases, not net revenue after refunds.
- RFM is descriptive; it does not establish the causal effect of marketing actions or predict future customer lifetime value.
- Segment definitions are rule-based and should be reviewed for the business context.

## Tools

Python, pandas, NumPy, Matplotlib, Seaborn, and Jupyter Notebook.
