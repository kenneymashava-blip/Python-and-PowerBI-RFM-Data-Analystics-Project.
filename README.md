# Python and PowerBI Recency Frequency and Monetary Data Analystics Project.
Welcome to the **RFM Data Analytics Project** repository!

This project focuses on data cleaning, and Frequency,Recency and Monetary analysis of the Kaggle's E-commerce dataset 
**[ecommerce_sales_customer_analytics_150k](https://www.kaggle.com/datasets/datascikhan/e-commerce-sales-and-customer-analytics?select=ecommerce_sales_customer_analytics_150k.csv)** using python's Pandas library,
and building of RFM Dashboard using Microsoft PowerBI.

## Tech Stack 
- Jupytper Notebook
- Python Libraries ( Pandas, Numpy, Matplotlib.plyplot and Seaborn)
- Microsoft PowerBI.
 
### This project is devided into three sections: 
- **Data cleaning and quality checks in python.**
- **RFM Analysis in python.**
- **Dashboard development in Microsoft PowerBI.**

## Data cleaning and quality checks in python.
The primary purpose of this section of the project is to clean the E-commerce csv dataset,
in preparation for Recency-Frequency-Monetary(RFM) Analysis in the next section of the project. 
The data cleaning process focuses on investigating the data quality problems,
which includes: 

- Checking for and replacing missing values where neccessary,
- Identification and removal of duplicated rows of records in the dataset,
- Rectifying incorrect datatypes such as dates,strings, float and integers,
- Save the final cleaned dataset as csv file.

## Recency Frequency Monetary(RFM) Analysis in python
The purpose of this section of the project is to perfom the Recency Frequency Monetary analysis using the cleaned E-Commerce csv file from the previous section.
The main steps taken include:

- Checking the data types quality issues in the dataframe.
- check for missing values.
- Set a reference date to perfom the Recency Frequency Monetary analysis. 
- Group the dataframe by Customer_Id, and perfom aggregations for recency,frequency and monetary using the order_date, order_id and gross sales.
- Calculate Recency Frequency Monetary Scores (Scale of 1-5 using 5 bins discretization).
- Classify or Segement the customers as **( Champions, Loyal Customers, Potenctial Loyalists, New Customers, At Risk, Lost and Others )** based on the RFM Scores.
- Save the final result as RFM_ csv file for dashboard development in PoweBI.
- Sketch countplots of the customer segments using Seaborn and matplotlib.pyplot to gain insights on the customer segments distributions.

## Customer Segmentation Summary

|Customer_Segment |	Total_Customers |	Total_Sales |	Percentage_Sales|
|:----------------|:----------------|:--------------|:------------------|
|At Risk| 	38 |	371779.56| 	0.20|
|Champions |	53 |	1307322.07 |	0.69|
|Lost |	176 |	403547.79 |	0.21|
|Loyal Customers| 	1016 |	17728336.64 |	9.33|
|New Customers |	11942 |	95068428.86 |	50.05|
|Others |	9212 |	42210988.80 |	22.22|
|Potential Loyal| 	2474 	|32872157.16 |	17.30|

## Dashboard development in PowerBI
In the PowerBi section, the RFM_E_Commerce.csv and Cleaned_E_Commerce.csv files from the prvious two sections of the project are loaded into PowerBi for dashboard development. The Dates_Table and Measures_Tables are constructed using DAX.The KPI's measures, variable recency,frequency and Monetary measures together with their respective color formating measures were developed and stored in the Measures_Table. The Star Schema model was developed using the Cleaned_E_Commerce as the fact table, and RFM_E_Commerce and Dates_table as the dimensions tables. Finally the Dashboard was developed using the model. 

## Dashboard Overview
https://github.com/user-attachments/assets/02e877ce-6cab-4be6-bb0d-010198001462

## References
**[Data with Baraa: PowerBI Ultimate Course](https://www.youtube.com/playlist?list=PLNcg_FV9n7qZge4KDGqGtqgiuVuhVZWzu)**

**[PivotalStats: Sales Dashboard in Power BI | RFM Analysis | End to End Project | Beginner Friendly](https://www.youtube.com/watch?v=XUygyGimSwI&t=4s)**

