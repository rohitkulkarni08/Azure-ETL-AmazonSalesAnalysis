# E-Commerce Sales Analysis and Optimization using Azure ETL Pipeline

## Overview

This project is centered around developing an extensive Extract, Transform, and Load (ETL) pipeline utilizing the advanced capabilities of Microsoft Azure. The pipeline efficiently retrieves data from Azure Blob Storage, performs necessary transformations using Azure Databricks and Azure Data Factory, and stores it in Azure Data Lake. It handles various data formats, including Delta and Parquet, ensuring flexibility and efficiency in data management. Additionally, the pipeline features a sales analysis component using PySpark within Azure Databricks, enabling comprehensive examination and analysis of sales data. The final analyzed data is securely stored in a SQL layer for subsequent use. This holistic solution streamlines the data processing workflow and provides actionable insights from the transformed and analyzed data, enhancing decision-making processes.

## Dataset

The [dataset](https://www.kaggle.com/datasets/thedevastator/unlock-profits-with-e-commerce-sales-data?select=Amazon+Sale+Report.csv) used in this project contains detailed information on e-commerce sales transactions for Amazon India, including customer demographics, product categories, order details, payment methods, and shipping information, allowing for in-depth analysis of sales patterns, customer behavior, and profitability in an e-commerce setting.

## Prerequisites

1. **Microsoft Azure Subscription**
2. **Azure Blob Storage**: A service providing scalable object storage for large amounts of unstructured data, ideal for storing images, videos, and other binary data.
3. **Azure Data Lake Gen2 Storage**: A highly scalable storage solution designed specifically for big data analytics, combining the capabilities of Azure Blob Storage and Azure Data Lake.
4. **Azure Databricks**: An advanced analytics platform based on Apache Spark, designed for big data processing, machine learning, and collaborative data science projects.
5. **Azure SQL Server**: A fully managed relational database service that utilizes the SQL Server engine to provide high-performance, reliable data storage and processing.
6. **Azure SQL Database**: A managed relational database service offering compatibility with the SQL Server engine, providing scalable and secure database solutions for modern applications.
7. **Azure Data Factory**: A comprehensive data integration service that allows for the creation, scheduling, and orchestration of ETL (Extract, Transform, Load) and ELT (Extract, Load, Transform) workflows, featuring a visually intuitive interface for building data-driven workflows to move and transform data at scale.


<img src="https://github.com/rohitkulkarni08/Azure-ETL-Pipeline-MovieAnalytics/blob/a0e8db3a6c03ef87bdfc023cd12e7c31da40ff17/images/azure_resource_group.png" width="1100" height="550">

## Data flow:

1. **Extract Data**: Retrieve CSV data from Azure Blob Storage for processing and load it to Azure Data Lake Storage Gen-2
2. **Transform Data**: Utilize PySpark on Azure Databricks to analyze and process the data, storing the results in Azure Data Lake Storage Gen2
3. **Load Data**: Transfer the processed data into an Azure SQL database to establish a reporting layer for dashboard creation
4. **Automation**: Construct end-to-end pipelines in Azure Data Factory to automate the data flow from extraction to reporting layers

<div style="text-align:center;">
  <img src="https://github.com/rohitkulkarni08/Azure-ETL-SalesAnalysis/blob/448cd5c2470797e4fbf528283daab39ce945e872/images/Flow.png" width = "900" height = "500">
</div>

## Setup and Configuration

### Azure Blob Storage
1. Create a container in your Azure Blob Storage account
2. Upload your input data files to the container

### Azure Data Lake Storage
1. Create a file system in your Azure Data Lake Storage account
2. Create a directory in the file system to store the processed Parquet files

### Azure Databricks
1. Create and configure a cluster with the necessary dependencies and settings for Python and PySpark.
2. In our case, I have used created a cluster with the configuration: 9.1 LTS (includes Apache Spark 3.1.2, Scala 2.12)
3. Create a new notebook in your Azure Databricks workspace

#### Azure SQL Database
1. Create a SQL database in Azure
2. Create the necessary tables in the database to store the processed data

#### Azure Data Factory
1. Create a new pipeline in your Azure Data Factory instance
2. Create a link service for each of the Azure functionalities used. I have created a Linked Service for: Azure Blob Storage, Azure Data Lake Gen2 Storage, Azure Databricks, and Azure SQL
3. Add activities to the pipeline for each step of the workflow:
   a. Data copy from Azure Blob Storage to Azure Data Lake Storage
   b. Data processing in Azure Databricks
   c. Data copy from Azure Data Lake Storage to Azure SQL Database
4. Running the Pipeline:
   a. Trigger the "Run All Pipelines" pipeline run in Azure Data Factory
   b. Monitor the pipeline run to ensure that each step completes successfully

### Pipeline #1: Copy Data from Blob to ADLS

<div style="text-align:center;">
  <img src= "https://github.com/rohitkulkarni08/Azure-ETL-SalesAnalysis/blob/448cd5c2470797e4fbf528283daab39ce945e872/images/blob-adls-pipeline.png" width = "600" height = "500">
</div>

### Pipeline #2: Trigger all Databricks Notebook Runs

<div style="text-align:center;">
  <img src= "https://github.com/rohitkulkarni08/Azure-ETL-SalesAnalysis/blob/448cd5c2470797e4fbf528283daab39ce945e872/images/databricks-pipeline.png">
</div>

### Pipeline #3: Copy Data from ADLS to SQL DB

<div style="text-align:center;">
  <img src= "https://github.com/rohitkulkarni08/Azure-ETL-SalesAnalysis/blob/448cd5c2470797e4fbf528283daab39ce945e872/images/sql-db-pipeline.png">
</div>

### Pipeline #4: Trigger all Pipelines

<div style="text-align:center;">
  <img src= "https://github.com/rohitkulkarni08/Azure-ETL-SalesAnalysis/blob/448cd5c2470797e4fbf528283daab39ce945e872/images/trigger-all-pipelines.png">
</div>

### Monitoring Pipeline Run

<div style="text-align:center;">
  <img src= "https://github.com/rohitkulkarni08/Azure-ETL-SalesAnalysis/blob/448cd5c2470797e4fbf528283daab39ce945e872/images/pipeline-run.png">
</div>

## Analysis

In this project, we conduct a comprehensive analysis of e-commerce sales data to gain insights into various aspects of the business. Our analysis covers six key areas: Statewise Sales Analysis, Categorywise Sales Analysis, Promotion Impact Analysis, Cancellation Impact Analysis, Size-wise Sales Analysis, and International Orders Analysis. Each analysis provides detailed metrics such as the number of orders, sales quantity, sales amount, and the impact of promotions and cancellations on sales. 

The data is further broken down by categories, sizes, and regions to understand customer preferences, regional sales trends, and the popularity of different products. This in-depth analysis helps in making informed decisions for inventory management, marketing strategies, and international expansion to optimize sales performance and cater to customer demands effectively.

### Analysis #1: Statewise Sales Analysis

This [analysis](https://github.com/rohitkulkarni08/Azure-ETL-SalesAnalysis/blob/448cd5c2470797e4fbf528283daab39ce945e872/output/csv/state-analysis.csv) provides a detailed breakdown of sales data across various states in India. It includes metrics such as the number of orders, sales quantity, total sales amount, average order quantity, and average sales amount per state. The data helps in understanding regional sales trends, customer preferences, and the overall performance of sales in different states, aiding in strategic decision-making for targeted marketing and sales optimization efforts 

### Analysis-2: Categorywise Sales Analysis

This [analysis](https://github.com/rohitkulkarni08/Azure-ETL-SalesAnalysis/blob/448cd5c2470797e4fbf528283daab39ce945e872/output/csv/category-analysis.csv) provides insights into sales data categorized by different types of apparel. It includes metrics such as the number of orders, sales quantity, total sales amount, average order quantity, and average sales amount for each category. This data helps in understanding the popularity and performance of each category, aiding in inventory management, marketing strategies, and product development to meet customer demands and preferences effectively.

### Analysis-3: Promotion Impact Analysis

This [analysis](https://github.com/rohitkulkarni08/Azure-ETL-SalesAnalysis/blob/448cd5c2470797e4fbf528283daab39ce945e872/output/csv/promotion-analysis.csv) examines the impact of promotions on sales across different apparel categories. It includes metrics such as the number of orders with and without promotions, quantity sold with and without promotions, the impact of promotions on quantity sold, sales with and without promotions, and the percentage impact of promotions on sales. This data helps in evaluating the effectiveness of promotional strategies, understanding the influence of promotions on customer purchasing behavior, and making informed decisions for future promotional campaigns to boost sales and revenue.

### Analysis-4: Cancellation Impact Analysis

This [analysis](https://github.com/rohitkulkarni08/Azure-ETL-SalesAnalysis/blob/448cd5c2470797e4fbf528283daab39ce945e872/output/csv/cancellation-analysis.csv) assesses the impact of order cancellations on sales across different apparel categories. It includes metrics such as the number of cancelled and not cancelled orders, cancelled and not cancelled quantity, the impact of cancellations on quantity, cancelled and not cancelled sales amount, and the percentage impact of cancellations on sales. This data helps in understanding the extent to which cancellations affect sales, identifying patterns or reasons behind cancellations, and developing strategies to minimize cancellations and their impact on overall sales and revenue.

### Analysis-5: Size-wise Sales Analysis

This analysis provides insights into sales data categorized by different sizes for various apparel categories. The data is presented in two tables:

**Size Sale Amount Analysis**:

This [analysis](https://github.com/rohitkulkarni08/Azure-ETL-SalesAnalysis/blob/448cd5c2470797e4fbf528283daab39ce945e872/output/csv/size-sales-analysis.csv) displays the sales amount for each size across different categories. The data helps in understanding the revenue generated from each size and identifying popular sizes among customers for each category.

**Size Sale Quantity Analysis**:

This [analysis](https://github.com/rohitkulkarni08/Azure-ETL-SalesAnalysis/blob/448cd5c2470797e4fbf528283daab39ce945e872/output/csv/size-quantity-analysis.csv) shows the quantity sold for each size across the same categories. It helps in analyzing the demand and popularity of specific sizes among customers, aiding in inventory management and production planning to meet the market demand effectively.

Overall, this size-wise sales analysis assists in making informed decisions regarding product sizing, inventory stocking, and marketing strategies to cater to customer preferences and optimize sales performance.

### Analysis-6: International Orders Analysis

This [analysis](https://github.com/rohitkulkarni08/Azure-ETL-SalesAnalysis/blob/448cd5c2470797e4fbf528283daab39ce945e872/output/csv/international-analysis.csv) focuses on international orders across different apparel categories and includes metrics such as the number of orders and sales amount for various categories that were shipped outside India. This data helps in understanding the global demand for different categories, aiding in strategic planning for international expansion and marketing efforts to capture a wider customer base and increase sales in the international market.
