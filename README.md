Project 2: 

Exploratory Data Analysis (EDA)
DecodeLabs Data Analytics Internship, Batch 2026

Problem Statement
Analyze a 1,200 row e-commerce order dataset to uncover patterns, trends, and outliers in order value, product performance, and revenue over time.

Tool Used
Microsoft Excel. All analysis is done with native formulas (no code), so every number recalculates automatically if the source data changes.

Dataset
1,200 orders, 14 columns: OrderID, Date, CustomerID, Product, Quantity, UnitPrice, ShippingAddress, PaymentMethod, OrderStatus, TrackingNumber, ItemsInCart, CouponCode, ReferralSource, TotalPrice. Only CouponCode has missing values (309 orders used no coupon, which is expected, not a data quality issue).

Methodology
The workbook (Project2_EDA.xlsx) has 6 tabs.

Data: raw dataset plus an outlier flag column, using IF and references to the Outliers tab.
Summary Stats: count, mean, median, std dev, min, max for the 4 numeric fields, using AVERAGE, MEDIAN, COUNT, STDEV.
Category Breakdown: order counts by Product, Status, Payment Method, and Referral Source, using COUNTIF.
Outliers: IQR based outlier bounds and the flagged orders, using QUARTILE, IF, OR.
Correlation: correlation matrix across the numeric fields, using CORREL.
Monthly Trend: revenue, order count, and average order value by month, with a line chart, using SUMIFS, COUNTIFS, EOMONTH.

Key Findings

Basic stats. Quantity: mean 2.95, median 3. Unit Price: mean $356.41, median $364.21. Items in Cart: mean 5.49, median 5. Total Price: mean $1,053.97, median $823.62.

Mean total price is well above the median, so the distribution is right skewed, meaning a handful of large orders pull the average up. Median is the more honest "typical order" figure here.

Outliers. 8 of 1,200 orders fall outside the IQR bounds (above $3,330.41), all clustered between $3,334 and $3,456. They span 5 different products (Printer, Laptop, Tablet, Chair, Monitor), not one product driving them, so these read as genuine large orders, not data errors.

Correlation. TotalPrice correlates most strongly with UnitPrice (r = 0.72) and Quantity (r = 0.62), which is expected since Total = Unit Price times Quantity. ItemsInCart correlates moderately with Quantity (r = 0.65) but only weakly with TotalPrice (r = 0.39), so cart size alone isn't a strong revenue predictor.

Product performance. Laptop has the highest average order value (around $1,111), Phone the lowest (around $973), about a 14% spread. Order volume is fairly even across all 7 products (156 to 181 orders each).

Order status. Nearly an even split: Cancelled 20.8%, Returned 20.6%, Pending 19.8%, Shipped 19.6%, Delivered 19.3%. About 41% of orders never successfully complete (Cancelled plus Returned), which is the most actionable finding in this dataset.

Monthly revenue. No strong seasonal pattern. Revenue fluctuates between roughly $29K and $53K per month with a slight uptick in mid 2025, but no clear trend across the 12 months covered.

Recommendation
The combined 41% cancel/return rate is the standout signal. Before optimizing marketing spend or product mix, it's worth investigating why orders are cancelled or returned (payment friction, shipping delays, product issues), since fixing that likely has more revenue impact than anything else visible in this data.
