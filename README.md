# Sport Product Sales Analysis
This Power BI project delivers a visually engaging and analytically detailed ad-hoc sales performance report for a sport product company. It allows users to explore how various product categories, regions, and seasonal-based trends affect business performance from revenue generation to profit tracking and sales forecasting.

![Sport Product Visualization](https://drive.google.com/uc?export=view&id=1yQ5_D5LQii85csTa7LP9k18qHI-kS1kA)

## Objective

- Analyze total sales and profit performance across product categories and months
- Compare month-on-month changes for sales, cost, profit, and units sold
- Identify trends in pricing and customer behavior
- Visualize regional performance and top/bottom-performing products

## Key Features

**KPI Cards** | Total Sales, Total Cost, Total Profit, Units Sold, Average Price |
**Month-on-Month (MoM) Analysis** | Trend visuals and color-coded insights on MoM % changes |
**Geo Performance** | Visual map of sales across regional locations, clustered bar chart of Sales and Profit by Region |
**Average Price Across States** | A matrix showing the average prices across states |
**Product Performance** | A table showing performance across different products |
**Channel Perfomance** | A table showing performance across the different sales channels |

## DAX highlights

**The dashboard used custom DAX measures to drive its dynamic visuals and KPIs**

-- PM (Previous Month)
-- MOM (Month on Month)

-- Total Sales
Total Sales = SUM('fct_Sport Products'[_Total Sales])

-- Month on Month Sales Change
Month on Month Sales =  
VAR PrevM = CALCULATE([_T Sales], DATEADD(dim_Calendar[Date],-1,MONTH))
VAR Total = [_T Sales]
RETURN
IF(AND(Total <> 0, PrevM <> 0),
    DIVIDE(Total - PrevM, PrevM, 0),
    BLANK()
)

-- Conditional Formatting Logic
Month on Month % SaleColor = IF([_MoMSales] >= 0, "Green", "Red")
Month on Month %Sale Background Color = IF([_MoMSales] >= 0, "#E6F5EE", "#FBEAE9")
Month on Month %Sale = IF([_MoMSales] >= 0, FORMAT([_MoMSales], "#.0%") & " ↗", FORMAT([_MoMSales], "#.0%") & " ↘")

**Similar logic is applied to cost, profit, price, and units sold to create a smooth and scalable analytics framework.**

## Tools & Technologies

- Power BI Desktop – data modeling, report design, visual storytelling

- DAX (Data Analysis Expressions) – for custom KPIs and advanced metrics

- Power Query – for data transformation

- Star Schema Design – optimized for performance and clarity

- Cardinality: one-to-many relationship 

## Sample Insights

- Men's footwear was the highest-selling product in Q1, with a revenue of around 5.8 million dollars 
- More people also purchased from outlet stores in Q1, while Online stores were the most patronized in Q4
- In December, Total sales increased by 26.5%, total profit increased by 27.4% from the previous month, and total units sold also increased by 9.9%,  which can be largely due to the holiday festivities.
- Products sold the most in Maine, United States of America, with a total revenue of $746,990 generated.

