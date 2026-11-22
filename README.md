# Python and Power BI Recency, Frequency, and Monetary Data Analytics Project

Welcome to the **RFM Data Analytics Project** repository!

This project focuses on data cleaning and recency, frequency, and monetary analysis of Kaggle's e-commerce dataset
[**ecommerce_sales_customer_analytics_150k**](https://www.kaggle.com/datasets/datascikhan/e-commerce-sales-and-customer-analytics?select=ecommerce_sales_customer_analytics_150k.csv) using Python's Pandas and building an RFM dashboard using Microsoft Power BI.

## Tech Stack

- Jupyter Notebook
- Python libraries: Pandas, NumPy, Matplotlib, and Seaborn
- Microsoft Power BI

### Project Sections

This project is divided into three sections:

- **Data cleaning and quality checks in Python**
- **RFM analysis in Python**
- **Dashboard development in Microsoft Power BI**

## Data Cleaning and Quality Checks in Python

The primary purpose of this section is to clean the e-commerce CSV dataset in preparation for recency, frequency, and monetary (RFM) analysis in the next section.

The data cleaning process focuses on investigating data quality problems, including:

- Checking for and replacing missing values where necessary
- Identifying and removing duplicated records in the dataset
- Rectifying incorrect data types, such as dates, strings, floats, and integers
- Saving the final cleaned dataset as a CSV file

## Recency, Frequency, and Monetary (RFM) Analysis in Python

The purpose of this section is to perform RFM analysis using the cleaned e-commerce CSV file from the previous section.

The main steps include:

- Checking the data types for quality issues in the dataframe
- Checking for missing values
- Setting a reference date to perform the RFM analysis
- Grouping the dataframe by `Customer_Id` and aggregating recency, frequency, and monetary values using `Order_Date`, `Order_Id`, and gross sales
- Calculating RFM scores on a scale from 1 to 5 using five-bin discretization
- Classifying or segmenting customers as **Champions, Loyal Customers, Potential Loyalists, New Customers, At Risk, Lost, or Others** based on the RFM scores
- Saving the final result as an RFM CSV file for dashboard development in Power BI
- Creating count plots of the customer segments using Seaborn and Matplotlib to gain insights into their distributions

## Customer Segmentation Summary

| Customer_Segment | Total_Customers | Total_Sales | Percentage_Sales |
|:-----------------|:----------------|:------------|:-----------------|
| At Risk | 38 | 371779.56 | 0.20 |
| Champions | 53 | 1307322.07 | 0.69 |
| Lost | 176 | 403547.79 | 0.21 |
| Loyal Customers | 1016 | 17728336.64 | 9.33 |
| New Customers | 11942 | 95068428.86 | 50.05 |
| Others | 9212 | 42210988.80 | 22.22 |
| Potential Loyal | 2474 | 32872157.16 | 17.30 |

## Dashboard Development in Power BI

In the Power BI section, the `RFM_E_Commerce.csv` and `Cleaned_E_Commerce.csv` files from the previous two sections are loaded into Power BI for dashboard development. The `Dates_Table` and measures are used to support the analysis and visualizations.

## Dashboard Overview

https://github.com/user-attachments/assets/02e877ce-6cab-4be6-bb0d-010198001462

## References

**[Data with Baraa: Power BI Ultimate Course](https://www.youtube.com/playlist?list=PLNcg_FV9n7qZge4KDGqGtqgiuVuhVZWzu)**

**[PivotalStats: Sales Dashboard in Power BI | RFM Analysis | End to End Project | Beginner Friendly](https://www.youtube.com/watch?v=XUygyGimSwI&t=4s)**
***
## About Me 👨‍🎓

I am a BSc Applied Mathematics and Statistics graduate with a passion for data science and analytics. This project reflects my ability to apply technical machine learning skills to real-world datasets.
