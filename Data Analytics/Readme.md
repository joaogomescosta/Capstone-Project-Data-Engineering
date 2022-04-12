# Data Analytics

## Overview

In this project was required to load data into a data warehouse in IBM DB2 and create a data source in Cognos that pointed to the database just created. It was necessary to design a reporting dashboard in Cogno Analytics that reflected the key metrics of the business of an e-commerce company.

## Objectives

- Create a dashboard using Cognos Analytics

## Tools / Software

- IBM Cognos Analytics
- Cloud instance of IBM DB2 database

## Environment setup

Download data from link: https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0321EN-SkillsNetwork/analytics/ecommerce.csv?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDB0321ENSkillsNetwork26764238-2021-01-01

### Import data
Import data in the file "ecommerce.csv" to DB2 into a table named sales_history
![dataimport](https://user-images.githubusercontent.com/95388763/162917964-4f567d5c-1b38-4b1c-a180-46620e49edf8.png)


### List top 10 rows
![top10rows](https://user-images.githubusercontent.com/95388763/162918124-6aa21d92-340e-400c-9d2e-ec532c67681f.png)


### Create a data source in Cognos that points to the table sales_history in DB2 database
![datasource](https://user-images.githubusercontent.com/95388763/162918280-fec53812-ba21-44b1-9a76-980b1d1ce2e0.png)


## Create dashboard

### Create a line chart
Create a line chart of month wise total sales for the year 2020
![linechart](https://user-images.githubusercontent.com/95388763/162918474-04e6ca40-cf52-43c9-b559-e8f3499dc162.png)


### Create a pie chart
Create a pie chart of category wise total sales.
![piechart](https://user-images.githubusercontent.com/95388763/162918698-d4bba54f-e72f-41b1-ae85-ef246bcd5605.png)


### Create a bar chart
Create a bar chart of Quarterly sales of mobile phones
![barchart](https://user-images.githubusercontent.com/95388763/162918861-29075e0b-80c4-4782-a864-45d2c0b9cd05.png)
