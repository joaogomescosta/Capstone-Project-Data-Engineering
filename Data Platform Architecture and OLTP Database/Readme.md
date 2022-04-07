# Data Platform Architecture and OLTP Database

## Overview
In this project was required to design the schema for a OLTP database to store data like row ID, product ID, customer ID, price, quantity, and time stamp for an e-commerce company and secondly to load  data into the OLTP database. Also was necessary to write a bash script that exported records created in the last 24 hours into another file.

## Objectives
- design the schema for OLTP database
- load data into OLTP database
- automate admin tasks

## Tools / Software

- MySQL 8.0.22
- phpMyAdmin 5.0.4
- Skills Network Labs Cloud IDE

## Design a table named sales_data on the sample data given by the company
![table 2](https://user-images.githubusercontent.com/95388763/162231277-23c3f931-e236-4dfc-af79-ee464a2c6398.png)

```
CREATE TABLE `sales`.`sales_data` (`product_id` INT NOT NULL , `customer_id` INT NOT NULL, `price` INT NOT NULL , `quantity` INT NOT NULL , `timestamp` TIMESTAMP NOT NULL ) ENGINE = InnoDB;
```

## Import the data from oltpdata.csv into sales_data table using phpMyAdmin
![importdata](https://user-images.githubusercontent.com/95388763/162233671-04e94055-0679-4b72-8145-99f8ad962502.png)

## List the tables in the database sales
```
SHOW FULL TABLES WHERE table_type = 'BASE TABLE';
```
## Write a query to find out the count of records in the tables sales_data
```
SELECT COUNT(*) FROM sales_data;
```
## Create an index named ts on the timestamp field and list List indexes on the table sales_data 
```
CREATE INDEX ts ON sales_data (timestamp);
SHOW INDEXES from sales_data;
```

## Write a bash script named datadump.sh that exports all the rows in the sales_data table to a file named sales_data.sql
```
# The beloow line tells the interpreter this codes needs to be run as a shell script
#!/bin/sh

# Set the database name to a variable
DATABASE='sales'
echo "Pulling sales_table: This may take a few minutes"

# Set the folder where the database backup will be stored
backupfolder=/home/theia/backups
sqlfile=$backupfolder/salesdata-$(date +%d-%m-%Y_%H-%M-%S).sql

# Create a backup
if mysqldump $DATABASE > %sqlfile ; then
    echo "SQL dump created"
    exit
fi
```
