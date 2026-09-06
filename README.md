# Sales Performance Dashboard (Excel)

## Project Overview

This project demonstrates an end-to-end sales analytics solution built entirely in Microsoft Excel using Power Query, Power Pivot, DAX, Pivot Tables, and an interactive dashboard. The project begins with intentionally dirty data, applies a structured cleaning and modeling process, and delivers actionable business insights through an executive-style dashboard. 【1-567be6】【2-e1ce3a】

\---

## Project Objectives

* Clean and transform messy sales data using Power Query.
* Build a dimensional data model using Power Pivot.
* Implement DAX measures for KPI calculations.
* Create interactive Pivot Tables and dashboard visualizations.
* Analyze sales performance across products, regions, channels, and salespeople. 【1-567be6】【2-e1ce3a】

\---

## Skills Demonstrated

### Data Preparation

* Power Query
* Data Cleaning
* Data Transformation
* Data Validation
* Missing Value Handling
* Duplicate Removal

### Data Modeling

* Star Schema Design
* Fact and Dimension Tables
* Power Pivot Relationships
* Calendar Table Creation
* Referential Integrity Management

### Analytics

* DAX Measures
* KPI Development
* Sales Performance Analysis
* Target Achievement Analysis

### Reporting

* Pivot Tables
* Pivot Charts
* Interactive Slicers
* Executive Dashboard Design 【1-567be6】【2-e1ce3a】

\---

# Dataset Structure

## Fact Table

### FactSalesData

Contains transactional sales data including:

* OrderID
* Date
* ProductKey
* RegionKey
* CustomerTypeKey
* MarketingChannelKey
* SalespersonKey
* Quantity

\---

## Dimension Tables

### DimDate

* Date
* Month
* Quarter
* Year

### DimProduct

* Product
* Category
* Unit Price
* Discount

### DimRegion

* Region

### DimSalesperson

* Full Name
* Job Title
* Hire Date
* Target
* Tenure Group

### DimCustomerType

* Customer Type

### DimMarketingChannel

* Sales Channel

The model follows a Star Schema design with FactSalesData at the center connected to all dimension tables through one-to-many relationships.

\---

# Data Cleaning Process

A structured data quality assessment was performed before developing the dashboard. 【1-567be6】

### Main Issues Identified

* Mixed capitalization
* Leading and trailing whitespace
* Mixed date formats
* Missing values
* Invalid foreign keys
* Duplicate transactions
* Category naming inconsistencies
* Missing sales targets 【1-567be6】

### Transformations Applied

* Trim
* Proper Case
* Replace Values
* Change Type
* Conditional Columns
* Column From Examples
* Append Queries
* Remove Duplicates 【1-567be6】

### Data Quality Decisions

* Missing HireDate values were preserved as null when a reliable replacement could not be determined.
* Invalid foreign keys were mapped to an Unknown dimension member (Key = 99) to preserve transactional records.
* Missing sales targets were imputed based on Job Title business rules.
* Tenure Groups were derived from HireDate for workforce performance analysis. 【1-567be6】

\---

# DAX Measures

## Total Revenue

```DAX
Total Revenue :=
SUMX(
    FactSalesData,
    FactSalesData\\\[Quantity]
        \\\* RELATED(DimProduct\\\[UnitPrice])
        \\\* (1 - RELATED(DimProduct\\\[Discount]))
)
```

## Total Orders

```DAX
Total Orders :=
DISTINCTCOUNT(FactSalesData\\\[OrderID])
```

## Total Quantity

```DAX
Total Quantity :=
SUM(FactSalesData\\\[Quantity])
```

## Average Order Value

```DAX
Average Order Value :=
DIVIDE(\\\[Total Revenue],\\\[Total Orders],0)
```

## Total Target

```DAX
Total Target :=
SUM(DimSalesperson\\\[TargetBasedOnTitle])
```

## Target Achievement %

```DAX
Target Achievement % :=
DIVIDE(\\\[Total Revenue],\\\[Total Target],0)
```

## Variance

```DAX
Variance :=
\\\[Total Revenue] - \\\[Total Target]
```

\---

# Dashboard KPIs

The dashboard reports the following key metrics:

* **Total Revenue:** $2.5M
* **Total Orders:** 1,993
* **Total Quantity Sold:** 5,528
* **Target Achievement:** 96% 【2-e1ce3a】

\---

# Dashboard Analysis

## Revenue by Region

Top performing regions:

1. North: approximately $557K
2. Central: approximately $555K
3. East: approximately $469K 【2-e1ce3a】

## Revenue by Category

Revenue is heavily concentrated in the Computers category.

* Computers: approximately $1.34M
* Monitors: approximately $528K
* Networking: approximately $255K 【2-e1ce3a】

## Revenue by Channel

Channel contribution:

* Online: 32%
* Corporate Sales: 30%
* Retail Store: 26%
* Marketplace: 13% 【2-e1ce3a】

## Top Selling Products

Top products by revenue:

1. Gaming Laptop ($415.8K)
2. All-in-One PC ($278.5K)
3. Laptop Pro 14 ($267.5K)
4. Laptop Air 13 ($265.5K)
5. Ultrawide Monitor ($214.7K) 【2-e1ce3a】

\---

# Salesperson Performance

### Top Performers

|Salesperson|Achievement|
|-|-|
|Aisha Lim|118%|
|Sofia Tan|114%|
|Kevin Yap|113%|
|Mei Tan|112%|
|Daniel Wong|108%|

### Lowest Achievement

|Salesperson|Achievement|
|-|-|
|Ben Ho|59%|
|Farah Ali|84%|
|Grace Ng|85%|

Overall team achievement reached **96% of target**. 【2-e1ce3a】

\---

# Tools Used

* Microsoft Excel
* Power Query
* Power Pivot
* DAX
* Pivot Tables
* Pivot Charts
* Slicers
* Timeline Controls 【2-e1ce3a】

\---

# Dashboard Preview

## Data Model


![data model] (images/data_model.png)



## Dashboard


![dashboard all data] (images/dashboard_all_data.png)



![dashboard central region] (images/dashboard_central_region.png)



![dashboard computers category] (images/dashboard_computers_category.png)


\---



# Key Takeaways

* Generated approximately **$2.5M** in revenue from **1,993** orders. 【2-e1ce3a】
* The **Computers** category was the primary driver of revenue. 【2-e1ce3a】
* **Online Sales** represented the largest sales channel. 【2-e1ce3a】
* **North** and **Central** regions delivered the strongest performance. 【2-e1ce3a】
* **Gaming Laptop** was the highest revenue-generating product. 【2-e1ce3a】
* Team performance reached **96% of target**, with several salespeople exceeding expectations. 【2-e1ce3a】

\---

*This project was created to demonstrate practical Excel Business Intelligence skills, including data cleaning, dimensional modeling, DAX calculations, and dashboard development.*

