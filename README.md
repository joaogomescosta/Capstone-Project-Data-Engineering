# Capstone Project Data Engineering

![data-engineering-on-azure](https://user-images.githubusercontent.com/95388763/162159677-75ad2ba6-5116-4231-9c93-54ae5ae99571.jpg)

## Project 1: Data Platform Architecture and OLTP Database

In this project was required to design the schema for a OLTP database to store data like row ID, product ID, customer ID, price, quantity, and time stamp for an e-commerce company and secondly to load  data into the OLTP database. Also was necessary to write a bash script that exported records created in the last 24 hours into another file.

Link: [Data Platform Architecture and OLTP Database](https://github.com/joaogomescosta/Capstone-Project-Data-Engineering/tree/main/Data%20Platform%20Architecture%20and%20OLTP%20Database)

## Project 2: NoSQL databases - MongoDB

In this assignment, an e-commerce company needed to design a data platform that used MongoDB as a NoSQL database to store catalog data. After importing the the data was necessary to create an indexe, make some queries and export selected fields from a collection into a csv file.

Link: [NoSQL databases - MongoDB](https://github.com/joaogomescosta/Capstone-Project-Data-Engineering/tree/main/NoSQL%20databases%20-%20MongoDB)

## Project 5: ETL and Data Pipelines using Apache AirFlow

In this project was necessary to develop a python script to keep data synchronized between different databases/data warehouses as a part of a daily routine in a e-commerce company. One task that is routinely performed was the sync up of staging data warehouse and production data warehouse. Automating this sync up will save a lot of time and standardize the process. A python script will perform the incremental data load from MySQL server which acts as a staging warehouse to the IBM DB2 which is a production data warehouse. Lastly a DAG was created in Airflow to perform several tasks. A pipeline was built that analyzes the web server log file, extracts the required lines and fields and transforms and load data.

Link: [ETL and Data Pipelines using Apache AirFlow](https://github.com/joaogomescosta/Capstone-Project-Data-Engineering/tree/main/ETL%20and%20Data%20Pipelines%20using%20Apache%20AirFlow)
