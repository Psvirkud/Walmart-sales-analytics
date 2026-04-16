# 🛍️ Walmart Sales Data Analysis

A comprehensive SQL-based analysis of Walmart sales data exploring customer behavior, sales patterns, product performance, and revenue metrics across multiple branches and cities.

## 📊 Project Overview

This project analyzes Walmart sales transactions to answer key business questions across four main dimensions:
- 🗺️ **Generic Insights**: Geographic distribution and branch locations
- 📦 **Product Analysis**: Product line performance and revenue contribution
- 👥 **Customer Insights**: Customer types, demographics, and purchasing patterns
- 📈 **Sales Performance**: Sales trends by time of day, customer type, and location

## � Project Files

- **walmart_sales.sql** - Complete SQL script with database/table creation and all analysis queries
- **WalmartSalesData.csv** - Sales transaction data (1000 records across 3 branches)
- **questions.txt** - List of analysis questions to be answered
- **README.md** - This documentation file

## �🗄️ Database Structure

### Database
- **Name**: `sales_walmart`

### Tables
- **sales**: Main transaction table containing all sales records

### Table Schema

| Column | Type | Description |
|--------|------|-------------|
| Invoice_id | VARCHAR(30) | Unique transaction identifier (Primary Key) |
| Branch | VARCHAR(50) | Store branch identifier |
| City | VARCHAR(30) | City where branch is located |
| Customer_type | VARCHAR(30) | Member or Non-member |
| Gender | VARCHAR(10) | Customer gender |
| Product_line | VARCHAR(100) | Category of product sold |
| Unit_price | DECIMAL(10,2) | Price per unit |
| Quantity | INT | Number of units sold |
| VAT | FLOAT(6,4) | Value Added Tax |
| Total | DECIMAL(12,4) | Total transaction amount |
| Date | DATETIME | Date of transaction |
| Time | TIME | Time of transaction |
| Payment_methods | VARCHAR(15) | Payment method used |
| COGS | DECIMAL(10,2) | Cost of Goods Sold |
| Gross_margin_percentage | FLOAT(11,9) | Gross margin percentage |
| Gross_income | DECIMAL(10,2) | Gross income |
| Rating | FLOAT(2,1) | Customer rating |
| Time_of_day | VARCHAR(20) | Morning/Afternoon/Evening (derived) |
| Day_name | VARCHAR(10) | Day of week (derived) |
| Month_name | VARCHAR(10) | Month name (derived) |

## ❓ Analysis Questions

### 🗺️ Generic Questions
- How many unique cities does the data have?
- In which city is each branch?

### 📦 Product Questions
- How many unique product lines does the data have?
- What is the most selling product line?
- What is the total revenue by month?
- What month had the largest COGS?
- What product line had the largest revenue?
- What is the city with the largest revenue?
- What product line had the largest VAT?

### 👥 Customer Questions
- How many unique customer types does the data have?
- How many unique payment methods does the data have?
- What is the most common customer type?
- Which customer type buys the most?
- What is the gender of most of the customers?
- What is the gender distribution per branch?

### 💰 Sales Questions
- Number of sales made in each time of the day per weekday?
- Which customer types bring the most revenue?
- Which city has the largest tax/VAT percent?
- Which customer type pays the most in VAT?

## 🔧 Key Derived Columns

The analysis includes three derived columns created through SQL transformations:

1. **time_of_day**: Categorizes transactions into time periods
   - Morning: 00:00:00 - 12:00:00
   - Afternoon: 12:01:00 - 16:00:00
   - Evening: 16:01:00 - 23:59:59

2. **day_name**: Extracts day of week from transaction date

3. **month_name**: Extracts month name from transaction date

## 💡 Usage

### Setup
1. Open `walmart_sales.sql` in your MySQL client (MySQL Workbench, phpMyAdmin, or command line)
2. Execute the entire script to:
   - Create the `sales_walmart` database
   - Create the `sales` table
   - Create derived columns (time_of_day, day_name, month_name)
3. The script will load structure; import the CSV data into the `sales` table using your MySQL client's import tool

### Data Import
- Use MySQL LOAD DATA INFILE or your client's import wizard to load `WalmartSalesData.csv` into the `sales` table
- Ensure the CSV columns map correctly to the table schema

### Answering Questions
- Refer to `questions.txt` for all analysis questions
- Each question has a corresponding SQL query in `walmart_sales.sql`
- You can:
  - Run individual queries to answer specific questions
  - Modify queries to filter by specific branches, time periods, or product lines
  - Combine results for deeper insights

### 📝 Example Query Structure
```sql
-- Question: What is the most selling product line?
SELECT
	SUM(quantity) as qty,
    product_line
FROM sales
GROUP BY product_line
ORDER BY qty DESC;
```

## ⭐ Features

✅ Multi-dimensional sales analysis  
✅ Temporal insights (time of day, day of week, month)  
✅ Customer demographic analysis  
✅ Product line performance metrics  
✅ Geographic sales distribution  
✅ Tax/VAT analysis across dimensions  

## 🔧 Requirements

- 🐬 MySQL 5.7 or higher
- 📄 WalmartSalesData.csv (included) with proper import tool
- 📚 Basic SQL knowledge to run and modify queries
- MySQL client (MySQL Workbench, phpMyAdmin, Command Line Client, etc.)

## 📁 Files

- 📜 `walmart_sales.sql` - Complete SQL script with all queries
- 📋 `questions.txt` - List of analysis questions
- 📖 `README.md` - This file

## 📌 Notes

- 💵 All monetary values are stored as DECIMAL for precision
- ⭐ Ratings are on a scale from 0.0 to 10.0
- ⏰ Time data includes both transaction time and derived time-of-day categorizations (Morning/Afternoon/Evening)
- 🏪 Analysis covers 3 branches across 3 cities (Yangon, Mandalay, Naypyitaw)
- 📊 Dataset contains 1000 transaction records from January-March 2019
- 💳 Five payment methods: E-wallet, Cash, Credit card

## 🚀 Future Enhancements

- 📊 Dashboard creation for visual insights
- 🔮 Predictive analytics for sales forecasting
- 🎯 Customer segmentation analysis
- 📅 Seasonal trend analysis
