#  Credit Card Data — Exploratory Data Analysis (EDA)

> A complete **Python-based EDA project** on PSPD Bank's credit card data covering customer acquisition, transactions, and repayments across 50+ countries.

---

##  Project Overview

This project answers key business questions for **Mr. Jim Watson (CEO, PSPD Bank)** using Exploratory Data Analysis on real credit card data. The goal is to understand customer spending & repayment behavior to evaluate fraud, bankruptcy, and collections — and to offer proactive customer service.

---

##  Dataset Description

Three CSV files are used in this project:

| File | Description |
|---|---|
| `Customer Acqusition.csv` | Customer details at card issuance — Age, City, Product, Limit, Segment |
| `spend.csv` | Transaction records — Customer, Month, Type, Amount |
| `Repayment.csv` | Payment records — Customer, Month, Amount |

---

## Q1 - Data Cleaning Rules Applied

| Rule | Logic |
|---|---|
| Age < 18 | Replace with **mean age** of all customers |
| Spend > Limit | Replace with **50% of customer's credit limit** |
| Repayment > Limit | Replace with the **customer's credit limit** |

---

##  Analysis Performed

###  Q2 — Summary Statistics
- Count of distinct customers
- Count of distinct spend categories
- Average monthly spend per customer
- Average monthly repayment per customer
- **Monthly Bank Profit** at 2.9% interest rate
  - `Monthly Profit = Monthly Repayment − Monthly Spend`
  - Interest earned **only on positive profits**
- Top 5 product types by spend
- City with maximum total spend
- Age group spending the most
- Top 10 customers by total repayment

###  Q3 — City-wise Yearly Product Spend
- Aggregated spend by **City × Product × Year**
- Bar/heatmap visualizations included

###  Q4 — Visualizations
| Chart | Details |
|---|---|
| Monthly City-wise Spend | Total spend per city for each month |
| Yearly Air Ticket Spend | Year-over-year comparison |
| Monthly Product Spend | Seasonality detection per product category |

###  Q5 — Custom Python Function
```python
top_customers_analysis(data=data, product='Gold', time_period='yearly')
```
- Takes **product** (`Gold` / `Silver` / `Platinum`) and **time_period** (`yearly` / `monthly`) as inputs
- Returns **Top 10 customers per city** ranked by repayment amount

---

##  Tech Stack

| Library | Version | Purpose |
|---|---|---|
| `pandas` | latest | Data loading, cleaning, aggregation |
| `numpy` | latest | Numerical operations |
| `matplotlib` | latest | Plotting and visualization |
| `seaborn` | latest | Enhanced statistical charts |
| `Jupyter Notebook` | — | Interactive analysis |

---

##  Repository Structure
```
credit-card-eda/
│
├── Credit_Card_Case_Study_.ipynb   ← Main solution notebook
├── Customer Acqusition.csv
├── spend.csv
├── Repayment.csv
└── README.md
```

---

##  How to Run

### 1. Clone the Repository
```bash
git clone https://github.com/vikasnagar31/credit-card-eda.git
cd credit-card-eda
```

### 2. Install Dependencies
```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### 3. Launch the Notebook
```bash
jupyter notebook Credit_Card_Case_Study_.ipynb
```

---

##  Key Insights from Analysis

---

###  Data Overview (Pre-cleaning)
- **Customer Acquisition table**: 100 records, 7 columns — no missing values, no duplicates
- **Spend (Transaction) table**: 1,500 records, 4 columns — no missing values, no duplicates
- **Repayment table**: 1,523 records — 23 rows had missing values and were dropped; no duplicates
- After merging all three tables, the final combined dataset had **37,284 rows and 12 columns**

---

###  Q1 — Data Cleaning Applied
- Ages below 18 were replaced with the **mean age** of all customers
- Spend amounts exceeding the credit limit were capped at **50% of the customer's limit**
- Repayment amounts exceeding the credit limit were capped at the **customer's credit limit**

---

###  Q2a — Distinct Customers
- **100 unique customers** exist in the dataset (A1 to A100)

---

###  Q2b — Distinct Spend Categories
- **15 unique spend categories** exist, including: JEWELLERY, PETRO, CLOTHES, FOOD, CAMERA, AIR TICKET, TRAIN TICKET, BIKE, AUTO, SHOPPING, BUS TICKET, and more

---

###  Q2c — Average Monthly Spend
| Month | Avg Spend (₹) |
|---|---|
| June | 1,85,539.52 |
| July | 1,72,496.04 |
| August | 1,71,892.47 |
| May | 1,61,558.55 |
| February | 1,59,385.15 |
| January | 1,55,942.99 |
| November | 1,55,925.32 |
| September | 1,54,158.23 |
| October | 1,42,427.17 |
| April | 1,38,957.48 |
| March | 1,38,588.31 |
| December | 1,14,736.24 |

> **June has the highest average monthly spend** and **December the lowest**

---

###  Q2d — Average Monthly Repayment
| Month | Avg Repayment (₹) |
|---|---|
| December | 2,00,137.98 |
| May | 1,94,271.47 |
| July | 1,84,579.33 |
| October | 1,82,892.19 |
| April | 1,71,751.83 |
| January | 1,68,675.75 |
| August | 1,67,324.07 |
| February | 1,66,728.01 |
| March | 1,60,361.67 |
| November | 1,58,510.80 |
| September | 1,38,239.38 |
| June | 1,17,505.96 |

> **December has the highest average repayment** — customers pay back the most after the holiday spending cycle

---

###  Q2e — Monthly Bank Profit (@ 2.9% interest)
> **Formula**: `Monthly Profit = Repayment − Spend` → Interest earned only on positive profit

Top profitable months:
| Month | Bank Profit (₹) |
|---|---|
| Jan 2004 | 1,17,45,010.85 |
| Feb 2005 | 72,25,199.58 |
| Mar 2006 | 75,08,206.02 |
| May 2005 | 94,70,060.91 |
| Apr 2006 | 44,42,337.52 |

> **January 2004** was the single most profitable month for the bank

---

###  Q2f — Top 5 Product (Spend) Types
| Rank | Category | Total Spend (₹) |
|---|---|---|
| 1 | CAMERA | 75,17,01,147 |
| 2 | PETRO | 70,71,54,853 |
| 3 | FOOD | 54,78,83,478 |
| 4 | AIR TICKET | 54,01,17,988 |
| 5 | TRAIN TICKET | 53,44,23,948 |

> **CAMERA and PETRO** dominate spending — together accounting for the largest share of all transactions

---

###  Q2g — City with Maximum Spend
- **CALCUTTA** has the highest average spend per transaction at ₹1,82,577.44

---

###  Q2h — Age Group Spending Analysis
| Age Group | Total Spend (₹) |
|---|---|
| **31–45** | **186 Crore** (Highest) |
| 18–30 | 158 Crore |
| 46–60 | 131 Crore |
| 60+ | 98 Crore |
| <18 | 0 (replaced with mean age) |

> The **31–45 age group spends the most**, making them the most valuable customer segment for targeted marketing

---

###  Q2i — Top 10 Customers by Repayment
| Rank | Customer | Total Repayment (₹) |
|---|---|---|
| 1 | A13 | 29,67,32,020 |
| 2 | A12 | 25,83,77,565 |
| 3 | A14 | 24,62,41,328 |
| 4 | A15 | 11,11,08,257 |
| 5 | A17 | 10,56,87,500 |
| 6 | A11 | 9,55,96,813 |
| 7 | A1 | 8,55,66,450 |
| 8 | A16 | 8,51,96,559 |
| 9 | A10 | 6,65,21,655 |
| 10 | A100 | 69,551 |

> **A13, A12, and A14** are the bank's top 3 most reliable repayers — prime candidates for premium credit offers

---

###  Q3 — City-wise Yearly Product Spend Highlights
- **Bangalore Gold** customers are the single largest spending group — ₹248 Cr (2004), ₹357 Cr (2005), ₹329 Cr (2006)
- **Calcutta Platinum** spend surged dramatically from ₹60 Cr (2004) to ₹132 Cr (2005)
- **Gold cardholders dominate** in almost every city compared to Silver and Platinum
- **Chennai and Trivandrum** are the only cities where Platinum spend rivals or exceeds Gold spend

---

###  Q4 — Visual Analysis Insights
- **Monthly City-wise Spend**: Calcutta consistently leads in per-transaction spend across all months
- **Yearly Air Ticket Spend**: Air ticket spending shows a year-on-year growth trend from 2004 to 2006
- **Monthly Product Seasonality**: Spending peaks in summer months (June–August) across most product categories, with a visible dip in December suggesting post-festive slowdown

---

###  Q5 — Custom Function: `top_customers_analysis()`
```python
# Example usage
top_customers_analysis(data=data, product='Gold', time_period='yearly')
```
- Successfully filters by product type (Gold / Silver / Platinum) and time period (yearly / monthly)
- Returns top 10 customers **per city** ranked by total repayment
- Example: For Gold cards (yearly), **A14 and A13 in Bangalore** and **A60 in Calcutta** consistently top the repayment charts across 2004–2006
---
