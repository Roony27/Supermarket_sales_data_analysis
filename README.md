# Supermarket_sales_data_analysis

## 📌 Project Overview
End-to-End Exploratory Data Analysis (EDA) on supermarket sales data using Python, Pandas, matplotlib,seaborn,jupyter and postgresql,pgadmin

## 🛠️ Tools & Technologies Used
* **Database:** PostgreSQL
* **Programming Language:** Python
* **Data Manipulation:** Pandas, NumPy, SQLAlchemy
* **Data Visualization:** Matplotlib, Seaborn
* **Security:** `python-dotenv` (for secure database credential management)

## 🧹 Methodology: Data Cleaning & Processing
To ensure data integrity before analysis, the following steps were performed:
* **Database Connection:** Established a secure connection to a PostgreSQL database using SQLAlchemy and environmental variables.
* **Data Type Conversion:** Converted `date` and `time` columns to appropriate datetime objects for accurate time-series analysis.
* **Duplicate Removal:** Checked and removed duplicate entries based on the `invoice_id`.
* **Feature Selection:** Dropped the `gross_margin_percentage` column as it contained a single constant value, offering no variance for statistical analysis.
* **Data Integrity Checks:** * Verified that critical numerical columns (`unit_price`, `total`, `tax`, `quantity`, `cogs`) contained no negative values.
  * Validated that customer ratings were strictly within the 0-10 range.
  * Performed mathematical validation on revenue calculations (e.g., verifying `Total = quantity * unit_price + tax` and `Total = cogs + gross_income`), utilizing rounding functions to successfully handle floating-point arithmetic errors.

## ⚙️ Feature Engineering
To enable deeper analysis, new features were created from the existing data:
* **Time Features:** Extracted `month` 'day', `month_name`, and `day_name` from the original date column to analyze seasonal and weekly trends.
* **Customer Segmentation:** Created a new categorical column (`total_cat`) using `pd.cut()` to classify transactions into "Low", "Medium", and "High" spending tiers.

## 📊 Key Business Insights
Through extensive data grouping and visualization, several crucial insights were discovered:
**1. The Profitability of the Membership Program**
* **Observation:** Customers enrolled in the membership program spend more on average per transaction ($327.79) compared to regular customers ($318.12). 
* **Recommendation:** The membership program is highly effective. The business should invest heavily in point-of-sale marketing campaigns (e.g., sign-up incentives at checkout) to convert 'Normal' customers into 'Members', thereby driving up total revenue.

**2. The Customer Satisfaction Disconnect (Revenue ≠ Loyalty)**
* **Observation:** Correlation analysis (via Heatmap) reveals a near-zero relationship between total transaction value and customer rating. Furthermore, the overall average rating is a mediocre 6.97/10. 
* **Recommendation:** Management must not mistake high sales volume for customer satisfaction. Customers are spending money, but they are not leaving excited. Qualitative investigations (e.g., post-purchase questionnaires) must be deployed to identify pain points and drastically improve the in-store experience.

**3. Operational Efficiency & Inventory Optimization**
* **Observation:** 'Food and beverages' is the flagship revenue driver ($56,144.84), while 'Health and beauty' lags behind ($49,193.73). Temporally, Saturdays and the month of January experience peak "traffic" (352 receipts), with a significant drop occurring in February (303 receipts).
* **Recommendation:** The supermarket can reduce operating expenses by dynamically adjusting staff shifts (e.g., increasing personnel on Saturdays and in January, while scaling back in February). Additionally, high-performing categories like 'Food and beverages' should be given prime, strategic shelf space.

**4. The Gender Spending Gap & Premium Upselling**
* **Observation:** Female customers consistently spend ~$25 more per visit than males. This trend persists regardless of membership status (Women members outspend men by $20.74; Normal female customers outspend males by $27.19). Interestingly, basket sizes are nearly identical (5.7 items for women vs. 5.3 for men). 
* **Recommendation:** The revenue gap does not come from women "buying more items," but rather from choosing premium or higher-margin products. Therefore, marketing strategies directed at women should focus purely on *upselling high-end items*. To recover the $25 "loss" from male shoppers, the store should introduce strategic bundles and cross-selling techniques near the cash registers.

**5. Paradigm Shift in Category Preferences & Targeted Merchandising**
* **Observation:** Breaking traditional stereotypes, male shoppers spend the absolute most in the 'Health and beauty' category (averaging ~$348), showing a massive difference compared to women (~$290). Men also dominate 'Sports and travel'. Women drive the revenue in 'Home and lifestyle' (~$380) and 'Food and beverages' (~$368).
* **Recommendation:** The business must abandon generic promotional campaigns and transition to *Targeted Marketing*. 'Health and beauty' and 'Sports' items should be placed in high-visibility impulse-buy areas specifically targeting men. Meanwhile, personalized campaigns (Emails/SMS for members) promoting 'Home & lifestyle' and 'Food' should be exclusively directed at the female demographic.

## 🚀 How to Run This Project Locally
**Option A: Using the provided CSV (Recommended for quick review)**
1. Clone this repository to your local machine.
2. Ensure you have the required libraries installed (`pip install pandas matplotlib seaborn`).
3. Open the Jupyter Notebook (`sales1.ipynb`).
4. Write `df_sales = pd.read_csv('supermarket_sales_RAW.csv')` to load the raw data directly, bypassing the SQL database connection.

