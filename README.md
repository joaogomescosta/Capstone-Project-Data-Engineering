# Capstone Project Data Engineering

![data-engineering-on-azure](https://user-images.githubusercontent.com/95388763/162159677-75ad2ba6-5116-4231-9c93-54ae5ae99571.jpg)

## Project 1: Data Platform Architecture and OLTP Database

In this project was required to design the schema for a OLTP database to store data like row ID, product ID, customer ID, price, quantity, and time stamp for an e-commerce company and secondly to load  data into the OLTP database. Also was necessary to write a bash script that exported records created in the last 24 hours into another file.

Link: [Data Platform Architecture and OLTP Database](https://github.com/joaogomescosta/Capstone-Project-Data-Engineering/tree/main/Data%20Platform%20Architecture%20and%20OLTP%20Database)

## Project 2: NoSQL databases - MongoDB

In this assignment, an e-commerce company needed to design a data platform that used MongoDB as a NoSQL database to store catalog data. After importing the data was necessary to create an index, make some queries and export selected fields from a collection into a csv file.

Link: [NoSQL databases - MongoDB](https://github.com/joaogomescosta/Capstone-Project-Data-Engineering/tree/main/NoSQL%20databases%20-%20MongoDB)

## Project 3: Data Warehousing and Data Warehousing Reporting
Data Warehousing
In this first part of the assignment, you will perform a couple of exercises. But before proceeding with the assignment, you will create an
instance of IBM DB2 on the cloud by following the instructions given in the link provided. If you have already created an instance in previous
labs, you can continue using that to perform the exercises. The first exercise requires you to design a data warehouse. The e-commerce
company has provided you with sample data. You will start your project by designing a Star Schema for the warehouse by identifying the
columns for the various dimension and fact tables in the schema. You will name your database as softcart and then use the ERD design tool to
design the table softcartDimDate using fields such as DateID, Month, Monthname, and so on. The company would like to have the ability to
generate the report on a yearly, monthly, daily, and weekday basis.
The following tasks require you to design the dimension tables softcartDimCategory, softcartDimCountry, and softcartFactSales using the
ERD design tool. Finally, you will use the ERD design tool to design the required relationships (one-to-one, one-to-many, and so on) amongst
the tables. After performing each task, you will take a screenshot of the entire ERD clearly showing all the field names, data types, and
relationships amongst the tables.
In the second exercise, you will load the data into the data warehouse. Your senior Data Engineer has reviewed your design and made a few
improvements to your schema design. The data as per the improved schema is available at a link. You will download the data and restore it
into a database named staging using the pgAdmin tool. After performing this task, you will take a screenshot showing the success of data
restoration.
Data Warehousing Reporting
In this second part of the assignment, you will perform a couple of exercises. But before proceeding with the assignment, you will create an
instance of IBM DB2 on the cloud by following the instructions given in the link provided. If you have already created an instance in previous
labs, you can continue using that to perform the exercises. The first exercise requires you to load the data provided by the company into the
tables in CSV format by performing a series of tasks. You will start by downloading the data from the links provided and then load that data
into the DimDate table, DimCategory table, DimCountry table, and fact table FactSales. After loading the data, you will take a screenshot of the
first five rows in each table and name the screenshot.
In the second exercise, you will query the loaded data by creating a grouping sets query, rollup query, and cube query using the columns
Orderid*, Category, and Price collected. Finally, you will create an MQT named Total_sales_per_country using the country and total sales
columns. After performing each task, you will take a screenshot of the SQL and the output rows and then name the screenshot.
Data Warehousing

The first exercise requires you to design a data warehouse. The e-commerce
company has provided you with sample data. You will start your project by designing a Star Schema for the warehouse by identifying the
columns for the various dimension and fact tables in the schema. You will name your database as softcart and then use the ERD design tool to
design the table softcartDimDate using fields such as DateID, Month, Monthname, and so on. The company would like to have the ability to
generate the report on a yearly, monthly, daily, and weekday basis.
The following tasks require you to design the dimension tables softcartDimCategory, softcartDimCountry, and softcartFactSales using the
ERD design tool. Finally, you will use the ERD design tool to design the required relationships (one-to-one, one-to-many, and so on) amongst
the tables. After performing each task, you will take a screenshot of the entire ERD clearly showing all the field names, data types, and
relationships amongst the tables.
In the second exercise, you will load the data into the data warehouse. Your senior Data Engineer has reviewed your design and made a few
improvements to your schema design. The data as per the improved schema is available at a link. You will download the data and restore it
into a database named staging using the pgAdmin tool. After performing this task, you will take a screenshot showing the success of data
restoration.
Data Warehousing Reporting
In this second part of the assignment, you will perform a couple of exercises. But before proceeding with the assignment, you will create an
instance of IBM DB2 on the cloud by following the instructions given in the link provided. If you have already created an instance in previous
labs, you can continue using that to perform the exercises. The first exercise requires you to load the data provided by the company into the
tables in CSV format by performing a series of tasks. You will start by downloading the data from the links provided and then load that data
into the DimDate table, DimCategory table, DimCountry table, and fact table FactSales. After loading the data, you will take a screenshot of the
first five rows in each table and name the screenshot.
In the second exercise, you will query the loaded data by creating a grouping sets query, rollup query, and cube query using the columns
Orderid*, Category, and Price collected. Finally, you will create an MQT named Total_sales_per_country using the country and total sales
columns. After performing each task, you will take a screenshot of the SQL and the output rows and then name the screenshot.

You are a data engineer hired by an ecommerce company named SoftCart.com . The company retails download only items like E-Books,
Movies, Songs etc. The company has international presence and customers from all over the world. The company would like to create a data
warehouse so that it can create reports like
total sales per year per country
total sales per month per category
total sales per quarter per country
total sales per category per country
You will use your data warehousing skills to design and implement a data warehouse for the company.

You are a data engineer hired by an ecommerce company named SoftCart.com . The company retails download only items like E-Books,
Movies, Songs etc. The company has international presence and customers from all over the world. You have designed the schema for the data
warehouse in the previous assignment. Data engineering is a team game. Your senior data engineer reviewed your design. Your schema design
was improvised to suit the production needs of the company. In this assignment you will generate reports out of the data in the data
warehouse.
## Project 5: ETL and Data Pipelines using Apache AirFlow

In this project was necessary to develop a python script to keep data synchronized between different databases/data warehouses as a part of a daily routine in a e-commerce company. One task that is routinely performed was the sync up of staging data warehouse and production data warehouse. Automating this sync up will save a lot of time and standardize the process. A python script will perform the incremental data load from MySQL server which acts as a staging warehouse to the IBM DB2 which is a production data warehouse. Lastly a DAG was created in Airflow to perform several tasks. A pipeline was built that analyzes the web server log file, extracts the required lines and fields and transforms and load data.

Link: [ETL and Data Pipelines using Apache AirFlow](https://github.com/joaogomescosta/Capstone-Project-Data-Engineering/tree/main/ETL%20and%20Data%20Pipelines%20using%20Apache%20AirFlow)
