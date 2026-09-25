# SWYNEX-Final-Data-Analytics-Project
## 📊 Sales Data Analytics — End-to-End Case Study

This project is a complete end-to-end **Data Analytics case study** developed as part of my internship with **SWYNEX Technologies**.

The project combines the work completed across:

* **Task 1 — Data Cleaning & Preparation**
* **Task 2 — Exploratory Data Analysis**
* **Task 3 — Interactive Power BI Dashboard**
* **Task 4 — Final Data Analytics Project**

The objective was to transform raw sales data into a clean, analyzed and interactive business intelligence solution.

---

## 🎯 Problem Statement

Raw sales data can contain missing values, duplicate records, inconsistent values and incorrect data types, making it difficult to perform reliable analysis.

The goal of this project was to:

* Clean and prepare the sales dataset
* Explore sales performance and identify patterns
* Analyze categories, products, states and monthly trends
* Build an interactive Power BI dashboard
* Extract meaningful business insights from the data
* Present the complete analytics workflow in one project

---

## 📌 Project Objectives

1. Clean and prepare the raw sales dataset.
2. Handle missing values, duplicates and data inconsistencies.
3. Perform exploratory data analysis using Python.
4. Identify important sales trends and patterns.
5. Create an interactive Power BI dashboard.
6. Present key business insights from the analysis.
7. Document the complete end-to-end analytics process.

---

## 📊 Dataset
### first
**Dataset:** Sales_transactions_2022_2025  - Dirty Data for Cleaning Training  
**Source:** Kaggle
**Period:** 2022–2025
**Rows:** 18,045 
**Columns:** 36
**Data type:** Raw, uncleaned transaction data
**About this file**
It is a Multi-Channel Retail & B2B Sales Transaction Dataset simulating sales of office equipment, electronics, furniture, appliances, and office supplies across multiple sales channels.
The dataset contains sales transactions with intentionally introduced data quality issues such as missing values, invalid entries, inconsistent values, and incorrect data types.

The notebook loads a cleaned and prepared CSV file named:

`Sales_transactions_2022_2025 cleaned & prepared.csv`

The dataset is expected to contain fields used in the notebook, including `Transaction_ID`, `Customer_Age`, `Quantity`, `Unit_Price`, `Discount_Percentage`, `Sales_Amount`, `Profit`, `Delivery_Days`, `Customer_Rating`, `Product_Category`, `Order_Year`, `Shipping_Method`, `Return_Reason`, `Customer_Segment`, `Promotion_Code`, `Region`, `Sales_Channel`, and `Payment_Method`.

**Note:** The CSV is not embedded in this notebook. Place it in your working directory or update the file path in the first notebook cell before running.

### Second
The project is based on a sales dataset containing ***848 records and 15 columns**.

| Column Name       | Description                                                                 |
|-------------------|-----------------------------------------------------------------------------|
| `title`           | Name or title of the mobile phone listed                                    |
| `ram`             | RAM specification of the mobile phone (e.g., 4GB, 6GB)                      |
| `brand`           | Brand name of the mobile phone (e.g., Samsung, Apple, Xiaomi)               |
| `url`             | Product listing URL on Flipkart                                             |
| `product_id`      | Unique identifier for each product                                          |
| `listing_id`      | Unique identifier for each product listing                                  |
| `highlights`      | Key features or highlights of the product                                   |
| `availability`    | Availability status (e.g., In Stock, Out of Stock, Coming Soon)             |
| `selling_price`   | Current selling price of the product                                        |
| `original_price`  | Original price before discount                                              |
| `currency`        | Currency used for pricing (e.g., INR ₹)                                     |
| `avg_rating`      | Average customer rating for the product                                     |
| `ratings_count`   | Total number of ratings received                                            |
| `reviews_count`   | Total number of customer reviews                                            |
| `one_stars_count` | Number of 1-star ratings                                                    |
| `two_stars_count` | Number of 2-star ratings                                                    |
| `three_stars_count`| Number of 3-star ratings                                                   |
| `four_stars_count`| Number of 4-star ratings                                                    |
| `five_stars_count`| Number of 5-star ratings   

The final cleaned dataset used for analysis is available in:

    `SWYNEX-Interactive-Dashboard Task 3.pbix`

# 🧹 Task 1 — Data Cleaning & Preparation
## Data Quality Issues Identified

The following issues were identified during the initial inspection:

- Missing values
- 'UNKNOWN' and 'ERROR' entries
- Incorrect data types
- Missing values in numeric and categorical fields
- Invalid or missing transaction dates
- Duplicate records check
- Fixing Typo

## 🧹 Data Cleaning Process

The dataset was cleaned and transformed using **Power Query**.

### Invalid Values

`UNKNOWN` and `ERROR` entries were identified and replaced with null values where applicable.

### Missing Values

Missing numeric values were handled using logical calculations wherever the required information was available.

For example, missing values were derived using the relationship between **Quantity,  Unit Price, and Sales Amount**.

Where a value could not be reliably determined, it was retained as Unknown rather than making assumptions.

Categorical missing values were also reviewed and retained as Unknown or Not Avl where no reliable value could be inferred.

### Data Types

Incorrect data types were identified and corrected to ensure that the dataset was properly structured and ready for analysis.

### Data Consistency

Categorical values were reviewed to ensure that invalid entries were removed and only valid values remained.

### Duplicate Records

The dataset was checked for duplicate records.

**Result**: 45 duplicate records were found.

### ➕ Calculated Columns Added

Four new calculated columns were created during preparation:

**Total Order Value-:>**
Formula: Quantity * Unit Price
Purpose: Ensures consistency between Quantity, Unit Price, and Sales Amount.

**Amount After Discount-:>**
Formula: Sales Amount - Discount
Purpose: Shows actual revenue after discounts.

**Charged Amount Percentage-:>**
Formula: Discount / Sales Amount (set to 0 if Sales Amount = 0)
Purpose: Helps analyze discount patterns across orders.

**Inventory Status-:>**
Formula: IF(Inventory Level > 0, "In Stock", "Out of Stock")

Purpose: Flags whether a product is available or out of stock for quick reporting.

### Transaction Date

The existing date values were already in the correct format, and the column data type was corrected to ensure it was properly recognized for analysis.

### Return Reason

Blanks replaced with "No Reason Provided".
If Return Flag = No → "Not Returned".
If Return Flag = Yes but blank → "Unspecified".

### Fixing Typos

Standardized categorical values (e.g., "Male" vs "Mle", "Retail" vs "Retaill").

Applied consistent casing (e.g., "Retail" instead of "retail").

Corrected spelling errors in Product Category, Sales Channel, and Order Status fields.

### Cleaning Script

The cleaning data is available in:

  `https://github.com/Malayasis-Banerjee/SWYNEX-Data-Cleaning-Preparation`

---

# 📈 Task 2 — Exploratory Data Analysis
After cleaning the dataset, exploratory data analysis was performed using Python.

The analysis focused on understanding:
## Analysis Workflow
1. **Load data** from the prepared CSV using pandas.
2. **Dataset overview & descriptive statistics** for selected numeric columns.
3. **Key performance indicators (KPIs):** total sales, total profit, overall profit margin, total quantity, and transaction count.
4. **Category and yearly aggregation:** normalize product-category labels and summarize sales/profit.
5. **Anomaly review:** count negative-profit transactions and calculate their average discount.
6. **Shipping analysis:** compare average customer rating, order count, and average delivery days by shipping method.
7. **Returns analysis:** count return reasons.
8. **Customer-segment analysis:** compare total/average sales, total/average profit, and quantity.
9. **Promotion analysis:** compare average sales, average profit, and transaction count by promotion code.
10. **Visualizations:** generate charts for yearly sales and profit, sales by product category, top 10 regions by sales, sales-channel distribution (donut chart), and sales by payment method.
    
## Key Performance Indicators

| KPI | Value |
|Total Sales Amount:| $8,234,090.60|
|Total Profit:| $1,645,439.40|
|Overall Profit Margin:| 19.98%|
|Total Units Sold:| 38,289|
|Total Transactions:| 18,001|

# 📊 Summary Statistics

This dataset contains **18,001 transactions** with customer demographics, product details, and sales metrics. Below is a statistical overview:

| Feature              | Count   | Mean     | Std Dev   | Min   | 25%   | 50%   | 75%   | Max    |
|----------------------|---------|----------|-----------|-------|-------|-------|-------|--------|
| **Customer Age**     | 18,001  | 38.92    | 10.66     | 4     | 32    | 39    | 46    | 112    |
| **Quantity**         | 18,001  | 2.13     | 1.78      | 0     | 1     | 2     | 3     | 11     |
| **Unit Price ($)**   | 18,000  | 232.78   | 294.25    | 21.39 | 52.96 | 99.85 | 285.78| 1425.09|
| **Discount (%)**     | 18,001  | 6.25     | 6.88      | 0     | 0     | 5     | 10    | 110    |
| **Sales Amount ($)** | 18,000  | 457.45   | 857.10    | 16.68 | 78.53 | 168.85| 472.74| 14303.07|
| **Profit ($)**       | 18,000  | 91.41    | 167.86    | -299.31| 19.49| 40.19 | 93.30 | 3512.08|
| **Delivery Days**    | 18,001  | 2.24     | 2.32      | 0     | 0     | 1     | 4     | 10     |
| **Customer Rating**  | 18,001  | 3.23     | 1.81      | 0     | 2     | 4     | 5     | 5      |

---

## 🔑 Key Insights
- Average customer age is **~39 years**, with a wide range (4–112).
- Most purchases involve **1–3 units**, but some go up to 11.
- Unit prices vary significantly, with a few high-value items ($1,425 max).
- Discounts are typically **0–10%**, but extreme cases reach 110%.
- Average sales amount is **$457**, but outliers push up to **$14,303**.
- Profit margins are positive on average, but some transactions show **losses**.
- Delivery is usually completed within **1–4 days**.
- Customer ratings cluster around **3–4 stars**, with some extremes at 0 and 5.

---

## 💡 Business Conclusion

This EDA provides a data-driven understanding of sales trends, revenue contribution, profitability, customer behavior, and operational performance. The analysis can help businesses identify areas for improvement, optimize sales and discount strategies, understand customer preferences, and make informed business decisions.

## 📊 Sales Analysis
### Visualizations
- Yearly Sales and Profit Trend (2022–2025)
  ![Yearly Sales and Profit Trend](yearly_trend.png)
- Total Sales by Product Category
  ![Total Sales by Product Category](category_sales.png)
- Top Regions by Sales Amount
  ![Top Regions by Sales Amount](regional_sales.png)
- Sales Distribution by Sales Channel
  ![Sales Distribution by Sales Channel](sales_channel_breakdown.png)
- Total Sales by Payment Method  
  ![Total Sales by Payment Method](https://github.com/Malayasis-Banerjee/SWYNEX-Exploratory-Data-Analysis/blob/main/Total%20Sales%20by%20Payment%20Method.png)

- Top 10 Best-Selling Items  
  ![Top 10 Best-Selling Items](https://github.com/Malayasis-Banerjee/SWYNEX-Exploratory-Data-Analysis/blob/main/Top%2010%20Best-Selling%20Items.png)

- Bottom 5 Underperforming Items  
  ![Bottom 5 Underperforming Items](https://github.com/Malayasis-Banerjee/SWYNEX-Exploratory-Data-Analysis/blob/main/bottom_5_underperforming_items.png)

  The exploratory analysis was performed using:

    `https://github.com/Malayasis-Banerjee/SWYNEX-Exploratory-Data-Analysis/blob/main/Task%202%20EDA.ipynb`

  # 📊 Task 3 — Interactive Power BI Dashboard

The cleaned dataset was then used to create an interactive dashboard in **Microsoft Power BI**.
### Dashboard Components

The dashboard includes:
## 🚀 Key Features

- **Executive KPIs**
  - Avg Selling Price: ₹17.24K  
  - Total Brands: 24  
  - Total Products: 329  
  - Avg Discount %: 11.86  
  - Total Ratings: 15.99M  
  - Total Reviews: 1.32M  

- **Interactive Modules**
  - Product Performance  
  - Customer Review Analysis  
  - Price & Discount Analysis  
  - Brand Analysis  
  - Extra Info  

- **Core Visuals**
  - 📈 Avg Selling Price by Brand  
  - ⭐ Avg Rating by Brand  
  - 🏆 Top Brands by Number of Mobiles  
  - 🎯 Availability Status Distribution (In Stock, Coming Soon, Out of Stock)  
  - 📊 Market Share of Top 10 Brands  
  - 🔍 Rating vs Review Correlation  

---
### Interactive Filters

Slicers were added to allow users to interactively filter and explore the sales data.

The Power BI dashboard file is available in:

`https://github.com/Malayasis-Banerjee/SWYNEX-Interactive-Dashboard`
---
## 🖼️ Dashboard Preview

This repository contains **five Power BI dashboards**, each focusing on a different aspect of analysis:

### `Product Performance` – Product sales and performance metrics
![Product_Performance](https://github.com/Malayasis-Banerjee/SWYNEX-Interactive-Dashboard/blob/main/Product%20Performance.png)
### `Customer Review Analysis` – Ratings, reviews, and sentiment insights 
![Customer Review Analysis](https://github.com/Malayasis-Banerjee/SWYNEX-Interactive-Dashboard/blob/main/Customer%20Review%20Analysis.png)
### `Price Discount Analysis` – Pricing strategies and discount impact 
![Price Discount Analysis](https://github.com/Malayasis-Banerjee/SWYNEX-Interactive-Dashboard/blob/main/Price%20And%20Discount%20Analysis.png)
### `Brand Analysis` – Market share and brand positioning  
![Brand Analysis](https://github.com/Malayasis-Banerjee/SWYNEX-Interactive-Dashboard/blob/main/Brand%20Analysis.png)
### `Extra Info` – Supporting data and additional insights  
![Extra info](https://github.com/Malayasis-Banerjee/SWYNEX-Interactive-Dashboard/blob/main/Extra%20Info.png)

## 📈 Analytical Insights

- **Discount Trap** → Excessive discounts (>20%) erode profit margins.  
- **Category Profit Paradox** → High revenue categories (e.g., Furniture in Superstore dataset) often yield low net profitability.  
- **Geographic Imbalances** → Certain regions outperform others, requiring targeted strategies.  
- **Seasonality** → Q4 spikes in sales highlight the importance of inventory and staffing optimization.

---
# 🔄 Project Workflow

```text
Raw Sales Data
      ↓
Data Cleaning & Preparation
      ↓
Cleaned Dataset
      ↓
Exploratory Data Analysis
      ↓
Key Findings & Insights
      ↓
Power BI Dashboard
      ↓
Final Business Insights
```

---

# 🛠️ Tools & Technologies

* **Python**
* **Pandas**
* **Jupyter / Python Environment**
* **Microsoft Power BI**
* **GitHub**
* **CSV**

---
# 📁 Project Structure

```text
SWYNEX-Final-Data-Analytics-Project
│
├── README.md
│
├── Dataset
│   └── sales_cleaned.csv
│
├── Data_Cleaning
│   └── clean_sales_data.py
│
├── EDA
│   └── Task 2 EDA.ipynb
│
├── Dashboard
│   └── SWYNEX_Interactive_Dashboard.pbix
│
└── Screenshots
    └── dashboard.png
```

---
# 🏁 Conclusion

This project demonstrates a complete **end-to-end data analytics workflow**, starting from data cleaning and preparation, followed by exploratory analysis and finally interactive dashboard development.

Through this project, I gained practical experience in:

* Data cleaning and preparation
* Exploratory data analysis
* Python and Pandas
* Business insight generation
* Power BI dashboard development
* Data visualization
* GitHub project documentation

The final outcome is a structured analytics solution that transforms sales data into meaningful insights through **Python analysis and an interactive Power BI dashboard**.

---
## ⚙️ How to View and Run Locally

### Prerequisites
- Install **Microsoft Power BI Desktop**

### Steps
1. Clone the repository:
   ```bash
     https://github.com/Malayasis-Banerjee/SWYNEX-Final-Data-Analytics-Project
   ```


## 👨‍💻 Internship Project

**Organization:** SWYNEX Technologies
**Project:** Final Data Analytics Project
**Domain:** Data Analytics
**Tools:** Python, Pandas, Power BI, GitHub

---

## 📌 Project Status

**Completed ✅**
## 👤 Author

**Malayasis Banerjee**  

Data Analyst Intern | Aspiring Data Analyst
#DataAnalytics #ExploratoryDataAnalysis #SWYNEXTechnologies
