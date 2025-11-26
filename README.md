📊 Sales Analytics Power BI Dashboard

A full end-to-end Sales Analytics Dashboard built in Power BI, covering KPI tracking, segmentation, profitability, regional insights, shipping performance, and multi-year sales trends.

<img src="Sales_Projects.png" width="100%" />
🚀 Project Overview

This dashboard analyzes several years of sales data and provides insights into:

Total Sales, Profit & Profit %

Year-over-Year (YoY) performance

Sales by Segment, Region, and Ship Mode

Geographical sales hotspots (Map)

Customer and Product analysis

Identification of the Star Product

Sales trends across 2016–2019

📂 Dataset Structure
Category	Fields
Sales	Sales, Quantity, Discount, Profit
Customer	Customer ID, Customer Name, Segment
Product	Product ID, Product Name, Category
Shipping	Ship Mode, Ship Date
Region	Country, State, City, Region
Date Table	Date, Year, Month, Quarter, Day, Weekend Flag

The project uses a Star Schema with Fact_Sales at the center and multiple dimension tables.

🧮 DAX Measures (Complete List)
▶️ Basic Metrics
Total Sales = SUM(Fact_Sales[Sales])

Total Quantity = SUM(Fact_Sales[Quantity])

Total Profit = SUM(Fact_Sales[Profit])

Profit % =
DIVIDE(
    [Total Profit],
    [Total Sales],
    0
)

▶️ Year-over-Year (YoY)
Sales LY =
CALCULATE(
    [Total Sales],
    SAMEPERIODLASTYEAR(Dim_Date[Date])
)

Sales YoY % =
DIVIDE(
    [Total Sales] - [Sales LY],
    [Sales LY],
    0
)

▶️ Customer & Product KPIs
Total Customers = DISTINCTCOUNT(Fact_Sales[Customer ID])

Total Products = DISTINCTCOUNT(Fact_Sales[Product ID])

▶️ Segment Analysis
Sales by Segment =
CALCULATE(
    [Total Sales],
    ALLEXCEPT(Dim_Customer, Dim_Customer[Segment])
)

Profit by Segment =
CALCULATE(
    [Total Profit],
    ALLEXCEPT(Dim_Customer, Dim_Customer[Segment])
)

▶️ Ship Mode Analysis
Sales by Ship Mode =
CALCULATE(
    [Total Sales],
    ALLEXCEPT(Dim_Shipping, Dim_Shipping[Ship Mode])
)

▶️ Region Insights
Sales by Region =
CALCULATE(
    [Total Sales],
    ALLEXCEPT(Dim_Region, Dim_Region[Region])
)

▶️ Star Product (Top Seller)
Star Product =
VAR ProductSales =
    ADDCOLUMNS(
        VALUES(Fact_Sales[Product Name]),
        "SalesValue", [Total Sales]
    )
VAR TopProduct =
    TOPN(1, ProductSales, [SalesValue], DESC)
RETURN
    CONCATENATEX(TopProduct, Fact_Sales[Product Name], ", ")

📊 Dashboard Visuals

Pie Chart: Sales by Segment

Bar Chart: Total Sales vs Sales LY (Year Trend)

KPI Tiles: Profit %, Total Sales, Customers, Products

Bar Chart: Sales by Ship Mode

Map Visualization: Geographic distribution of sales

Area Chart: Sales by Segment & Region

Highlight Card: Star Product

🎨 UI/UX Design Elements

Gradient blue–purple background

Rounded containers for clean layout

Bright KPI tiles for fast insight

Region-colored map for geospatial storytelling

Smooth professional theme suitable for portfolios

🔍 Key Insights

The Consumer segment drives the largest share of revenue

Profit margin ~25%

Economy ship mode accounts for most sales volume

Europe (Germany, France, UK) is the strongest market

YoY Sales increased steadily

Star Product: Hoover Stove, White

📁 Project Structure
📦 Sales Analytics Dashboard
│
├── README.md
├── Sales_Projects.png
├── Sales_Analytics.pbix
│
└── Dataset/
    ├── Sales.csv
    ├── Customers.csv
    ├── Products.csv
    ├── Regions.csv
    └── Calendar.csv

🧠 Skills Demonstrated

Power BI (Power Query, DAX, Data Modeling)

Data Warehousing & Star Schema modeling

KPI + performance calculations

Geospatial analytics (Map visual)

UX-focused dashboard design

Business insights and storytelling

End-to-end reporting delivery
