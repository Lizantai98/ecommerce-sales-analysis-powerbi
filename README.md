# E-commerce Sales Analysis | Power BI Dashboard

A three-page Power BI dashboard analysing 60,398 sales lines, 18,484 customers and 295 products from December 2010 to January 2014. It answers three questions: how the business is performing, who the customers are, and which products sell and earn.

### Data Model

<img width="1176" height="769" alt="image" src="https://github.com/user-attachments/assets/562b1a91-a877-49ef-b808-c43b7cf545ae" />


## Business Questions
- How have revenue, profit and orders changed over time?
- Who are the customers, and how much value do they bring?
- Which products and categories drive revenue and profit?

## Dataset
Three tables: fact_sales, dim_customers and dim_products. This is the same dataset I analysed in my SQL and Excel projects.

## Tools
Power BI Desktop: Power Query, DAX and data modelling.

## Data Preparation
- Cleaned text columns, set the correct data types and replaced "n/a" placeholders with blanks
- Created a full name column for customers
- Built a Calendar table and a star schema: fact_sales linked to dim_customers, dim_products and Calendar
- Added customer columns for spend segment (based on lifetime revenue), age group and first order year

## Selected DAX Measures

- Avg Order Value = DIVIDE([Total Revenue], [Total Orders])

- Repeat Customers = COUNTROWS(FILTER(dim_customers, CALCULATE(DISTINCTCOUNT(fact_sales[order_number])) > 1))

- VIP Customers = COUNTROWS(FILTER(dim_customers, [Total Revenue] >= 5000))

- Revenue Share by Segment = DIVIDE([Total Revenue], CALCULATE([Total Revenue], ALLSELECTED(dim_customers[Spend Segment])))

- Bikes Share = DIVIDE(CALCULATE([Total Revenue], dim_products[category] = "Bikes"), CALCULATE([Total Revenue], ALL(dim_products[category])))

## Key findings

### Overview

<img width="1452" height="848" alt="image" src="https://github.com/user-attachments/assets/9a1658fc-ad2c-485f-94ff-fad1d0822e1c" />


- Revenue is 29.4M with 11.7M profit, a 39.8% margin.
- Revenue went from 7.1M (2011) to 5.8M (2012) to 16.3M (2013).
- In 2013, orders grew 6.5x (3,269 to 21,287) but revenue only 2.8x, because the average order value fell from 1,787 to 768 as low-priced accessories and clothing launched.
- Accessories are 59.8% of units sold but only 2.4% of revenue. Bikes are 96.5% of revenue.
- The United States and Australia together generate about 62% of revenue.

### Customer Analysis

<img width="1442" height="853" alt="image" src="https://github.com/user-attachments/assets/f14b406f-dbac-46f1-a1da-10567a19067f" />


- 37.1% of customers ordered more than once.
- The 1,732 VIP customers (9.4% of the base, lifetime spend of 5,000 or more) produce 38.3% of revenue, while the 50.4% with the lowest spend produce 2.0%.
- Australia earns 2,523 per customer, about twice the United States (1,225).
- The ten highest-spending customers are all in France, with 12,914 to 13,294 each.
- New customers (by first purchase) jumped from 3,225 in 2012 to 12,521 in 2013.

### Product Analysis

<img width="1442" height="853" alt="image" src="https://github.com/user-attachments/assets/bfda066a-406d-4fcc-8d01-dbb690e6cded" />


- Mountain Bikes have the best bike margin (43.8%, against 36.5% for Road Bikes), and Mountain overtook Road as the top product line in 2013.
- Caps and Jerseys earn only 22% to 23% margin, against 62% to 67% for other accessories.
- Only 130 of the 295 catalogue products (44.1%) were ever sold.
- The top 10 products are all Mountain-200 or Road-150 bikes.

## Notes
- 2010 and 2014 contain only one month of sales each, so year comparisons focus on 2011 to 2013.
- Shipping time is exactly 7 days for every order, so it is not analysed.
- The customer creation date in the source falls in 2025 and 2026, after the sales period, so new customers are based on first purchase date instead.
- Spend segments and first order year use lifetime data and do not change with the year filter.

## Author

Elizabeth Antai, Data Analyst [LinkedIn](https://www.linkedin.com/in/elizabeth-antai/) | [GitHub](https://github.com/Lizantai98)
