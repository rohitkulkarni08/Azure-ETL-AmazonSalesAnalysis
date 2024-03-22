# End-to-End ETL Pipeline with Microsoft Azure for IMDb Movie Rating Dataset

## Overview

This project focuses on building a comprehensive Extract, Transform, and Load (ETL) pipeline leveraging the robust functionalities of Microsoft Azure. The pipeline is designed to efficiently fetch data from Azure Blob Storage perform necessary transformations using Azure Databricks and Azure Data Factory, store it in Azure Data Lake and finally store the analyzed data in a SQL layer for further use. This end-to-end solution aims to streamline the data processing workflow and provide actionable insights from the transformed data.

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
  <img src="" width = "900" height = "500">
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
   a. Data processing in Azure Databricks
   b. Data copy from Azure Data Lake Storage to Azure SQL Database

<div style="text-align:center;">
  <img src= "" width = "600" height = "400">
</div>

4. Running the Pipeline:
   a. Trigger the pipeline run in Azure Data Factory
   b. Monitor the pipeline run to ensure that each step completes successfully

<img src= "g">

### Analysis #1: 

We perform language-based analysis on a movie dataset, focusing on non-numeric original language entries. We generate a summary dataframe that includes the number of movies, average budget, average revenue, and average popularity for each language. This analysis helps in understanding the impact of the original language on various movie metrics

### Analysis #2: Release Date Analysis

We analyze movies released after 1995 in the dataset. We calculate the number of movies released per year and perform a genre analysis to identify the top 5 genres for each year. The final output summarizes the number of movies released and the top 5 genres for each year post-1995

### Analysis #3: Genre Analysis

We conduct a comprehensive analysis of movie genres in the dataset. We calculate the distribution of genres and aggregates the average budget, revenue, rating, and popularity for each genre. The final output summarizes the average budget, revenue, rating, popularity, and the number of movies for each genre, providing insights into the characteristics and trends of different movie genres
