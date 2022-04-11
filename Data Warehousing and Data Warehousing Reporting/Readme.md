# Data Warehousing and Data Warehousing Reporting

## Overview

In this project was required to design a data warehouse to an e-commerce company which provided a sample data to design a star schema, the design was accomplished by using an ERD tool. A second part of the assignment, consisted in loading the data provided by the company into the tables in CSV format, perform a set of aggregation queries for data analitycs (grouping sets, rollup, cube) and create a MQT.

## Objectives

- Design a Data Warehouse using the pgAdmin ERD design tool
- Create the schema in the Data Warehouse
- Load data into Data Warehouse
- Write aggregation queries
- Create MQTs

## Tools / Software

- ERD Design Tool of pgAdmin
- PostgreSQL Database Server
- Cloud instance of IBM DB2 database
- Skills Network Labs Cloud IDE

### Design a Data Warehouse with the sample data provided below
![aaaa](https://user-images.githubusercontent.com/95388763/162710885-458ed358-f3f7-479d-bcab-4e7bf9146c71.png)



### Design the dimension table softcartDimDate
![softcartDimDate](https://user-images.githubusercontent.com/95388763/162711168-37cfffa6-16ed-4152-8797-3fcdd4e251a9.png)



### Design the dimension table softcartDimCategory
![softcartDimCategory](https://user-images.githubusercontent.com/95388763/162711229-66db9f80-f848-4ccc-be3c-4efa40f60071.png)



### Design the dimension table softcartDimItem
![softcartDimItem](https://user-images.githubusercontent.com/95388763/162711294-4ecf0e7d-8920-469b-9c73-51183d77871a.png)



### Design the dimension table softcartDimCountry
![softcartDimCountry](https://user-images.githubusercontent.com/95388763/162711356-56c10f3d-91d0-4a3e-bdff-5bd113f68e36.png)



### Design the fact table softcartFactSales
![softcartFactSales](https://user-images.githubusercontent.com/95388763/162711507-6b393307-ffa7-4eb7-8950-e12c414da98d.png)



### Design the relationships
![softcartRelationships](https://user-images.githubusercontent.com/95388763/162711600-3d2cc628-9144-4326-8aef-bb3d9e5dd94d.png)



### Create the schema in a database named staging
![createschema](https://user-images.githubusercontent.com/95388763/162711811-4fd1b70f-4f34-44a8-b68a-1cb45ab99d87.png)



### Load data into the Data Warehouse IBM DB2 in csv format
Download data from this link : https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0321EN-SkillsNetwork/datawarehousing/DimDate.csv?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDB0321ENSkillsNetwork26764238-2021-01-01



### Load data into the dimension table DimDate
![DimDate](https://user-images.githubusercontent.com/95388763/162712887-9d3bcd5a-01f6-447a-a9d3-acd74a3e15f0.png)



### Load data into the dimension table DimCategory
![DimCategory](https://user-images.githubusercontent.com/95388763/162712962-a538e5ff-8c37-43fa-a2ec-d81be2e67457.png)



### Load data into the dimension table DimCountry
![DimCountry](https://user-images.githubusercontent.com/95388763/162712974-0353a10f-236d-4381-a414-3f838e185df8.png)



### Load data into the fact table FactSales
![FactSales](https://user-images.githubusercontent.com/95388763/162713032-387f0a05-3a99-4ba3-86ce-9a493a150d80.png)



### Create a grouping sets query
Create a grouping sets query using the columns country, category, totalsales.
![groupingsets](https://user-images.githubusercontent.com/95388763/162713205-988d7830-1e83-4578-bb5b-d0c01e8794b1.png)



### Create a rollup query
Create a rollup query using the columns year, country, and totalsales.
![rollup](https://user-images.githubusercontent.com/95388763/162713336-c2c4f135-ccf8-4a40-9a02-eaca61e9022c.png)



### Create a cube query
Create a cube query using the columns year, country, and average sales.
![cube](https://user-images.githubusercontent.com/95388763/162713469-5a963a98-a4bf-4dea-88fa-9968c51de208.png)



### Create an MQT
Create an MQT named total_sales_per_country that has the columns country and total_sales.
![mqt](https://user-images.githubusercontent.com/95388763/162713543-6d313000-aba7-45f9-bfc4-9cf4b3e3cebf.png)
