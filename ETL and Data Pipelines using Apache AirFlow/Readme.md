# ETL and Data Pipelines using Apache AirFlow

## Overview

In this project was necessary to develop a python script to keep data synchronized between different databases/data warehouses as a part of a daily routine in a e-commerce company. One task that is routinely performed was the sync up of staging data warehouse and production data warehouse. Automating this sync up will save a lot of time and standardize the process. A python script will perform the incremental data load from MySQL server which acts as a staging warehouse to the IBM DB2 which is a production data warehouse. Lastly a DAG was created in Airflow to perform several tasks. A pipeline was built that analyzes the web server log file, extracts the required lines and fields and transforms and load data. 

## Objectives

Write a python program that will:
- Connect to IBM DB2 data warehouse and identify the last row on it.
- Connect to MySQL staging data warehouse and find all rows later than the last row on the datawarehouse.
- Insert the new data in the MySQL staging data warehouse into the IBM DB2 production data warehouse.

Author an Apache Airflow DAG that will:
- Extract data from a web server log file
- Transform the data
- Load the transformed data into a csv file

## Tools / Software

- MySQL Server
- IBM DB2 database running on IBM Cloud
- Apache AirFlow
- Skills Network Labs Cloud IDE

### Start MySQL server
```
start_mysql
```

### Create a database named sales
```
# go to CLI
mysql --host=127.0.0.1 --port=3306 --user=root --password=******
create database sales;
use sales;
```
### Download the file below
```
wget https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0321EN-SkillsNetwork/ETL/sales.sql
```
### Import the data in the file sales.sql into the sales database
```
source sales.sql;
```
### Download the file below
```
wget https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0321EN-SkillsNetwork/ETL/sales.csv
```
### Load sales.csv into a table named sales_data on cloud instance of IBM DB2 database
![sales data](https://user-images.githubusercontent.com/95388763/162425785-0e2cf749-417a-4087-bccf-59adeacfc0d9.png)

### Automate loading of incremental data into the data warehouse
```
# Import libraries required for connecting to mysql
# pip3 install mysql-connector-python
import mysql.connector

# Import libraries required for connecting to DB2
# pip3 install ibm-db
import ibm_db
 
# Connect to MySQL
connection = mysql.connector.connect(user='root', password='******',host='127.0.0.1',database='sales')

# create cursor
cursor = connection.cursor()

# Connect to DB2
# connection details
dsn_hostname = "55fbc997-9266-4331-afd3-888b05e734c0.bs2io90l08kqb1od8lcg.databases.appdomain.cloud"
dsn_uid = "rwm48321"        
dsn_pwd = "******"      
dsn_port = "31929"               
dsn_database = "bludb"            
dsn_driver = "{IBM DB2 ODBC DRIVER}"         
dsn_protocol = "TCPIP"            
dsn_security = "SSL"              

#Create the dsn connection string
dsn = (
    "DRIVER={0};"
    "DATABASE={1};"
    "HOSTNAME={2};"
    "PORT={3};"
    "PROTOCOL={4};"
    "UID={5};"
    "PWD={6};"
    "SECURITY={7};").format(dsn_driver, dsn_database, dsn_hostname, dsn_port, dsn_protocol, dsn_uid, dsn_pwd, dsn_security)

# create connection
conn = ibm_db.connect(dsn, "", "")
print ("Connected to database: ", dsn_database, "as user: ", dsn_uid, "on host: ", dsn_hostname)

# Find out the last rowid from DB2 data warehouse
# The function get_last_rowid must return the last rowid of the table sales_data on the IBM DB2 database.
def get_last_rowid():
    last_rowid = "SELECT rowid from sales_data ORDER BY rowid DESC fetch first 1 row only"
    stat_last_rowid = ibm_db.exec_immediate(conn, last_rowid)
    while ibm_db.fetch_row(stat_last_rowid) != False:
        return ibm_db.result(stat_last_rowid, 0)

last_row_id = get_last_rowid()
print("Last row id on production datawarehouse = ", last_row_id)

# List out all records in MySQL database with rowid greater than the one on the Data warehouse
# The function get_latest_records must return a list of all records that have a rowid greater than the last_row_id in the sales_data table in the sales database on the MySQL staging data warehouse.
def get_latest_records(last_row_id):
    rowid = "SELECT * from sales_data WHERE rowid > %(rowid)s ORDER BY rowid;"
    cursor.execute(rowid, {'rowid': last_row_id})
    latest_records = list(cursor.fetchall())
    return latest_records

new_records = get_latest_records(last_row_id)
print (new_records)

print("New rows on staging datawarehouse = ", len(new_records))

# Insert the additional records from MySQL into DB2 data warehouse.
# The function insert_records must insert all the records passed to it into the sales_data table in IBM DB2 database.
def insert_records(records):
    from datetime import datetime
    sql = "INSERT INTO sales_data (rowid, product_id, customer_id, quantity, price, timestamp) VALUES (?,?,?,?,?,?)"
    stmt = ibm_db.prepare(conn, sql)
    for row in records:
        timestamp = datetime.now().strftime("%Y-%m-%d %H:%M:%S")
        row = tuple(list(row) + [None, timestamp])
        ibm_db.execute(stmt, row)
      
insert_records(new_records)
print("New rows inserted into production datawarehouse = ", len(new_records))

# disconnect from mysql warehouse
connection.close()

# disconnect from DB2 data warehouse
ibm_db.close(conn)

# End of program
```
### Start Apache Airflow
```
start_airflow
```
### Download the dataset from the source to the destination
```
wget -P /home/project/airflow/dags/capstone https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0321EN-SkillsNetwork/ETL/accesslog.txt
```
### Create a DAG that does the folowing tasks:
- Task 1 - This task should extract the ipaddress field from the web server log file and save it into a file named extracted_data.txt
- Task 2 - This task should filter out all the occurrences of ipaddress "198.46.149.143" from extracted_data.txt and save the output to a file named
transformed_data.tx
- Task 3 - This task should archive the file transformed_data.txt into a tar file named weblog.tar
```
# import the libraries
from datetime import timedelta

# The DAG object; we'll need this to instantiate a DAG
from airflow import DAG

# Operators; we need this to write tasks!
from airflow.operators.bash_operator import BashOperator

# This makes scheduling easy
from airflow.utils.dates import days_ago

# Defining DAG arguments
default_args = {
	'owner': 'Joao Costa',
	'start_date': days_ago(0),
	'email': ['cristiano_ronaldo@cr7.com'],
	'email_on_failure': True,
	'email_on_retry': True,
	'retries': 1,
	'retry_delay': timedelta(minutes=5),
}

# Define the DAG
dag = DAG(
	dag_id='process_web_log',
	default_args=default_args,
	description='ETL DAG using Bash',
	schedule_interval=timedelta(days=1),
)



# Create task 1 - This task should extract the ipaddress field from the web server log file and save it into a file named extracted_data.txt
extract = BashOperator(
	task_id='extract_data',
	bash_command='grep -E -o "(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)" accesslog.txt > extracted_data.txt',
	dag=dag,
)


# Create task 2 -  This task should filter out all the occurrences of ipaddress "198.46.149.143" from extracted_data.txt and save the output to a file named
transformed_data.tx
transform = BashOperator(
	task_id='transform_data',
	bash_command='grep -v 198.46.149.143 extracted_data.txt > transformed_data.txt',
	dag=dag,
)

# Create task 3 - This task should archive the file transformed_data.txt into a tar file named weblog.tar
load = BashOperator(
	task_id='load_data',
	bash_command='tar -zcvf weblog.tar.gz transformed_data.txt',
	dag=dag,
)


# Define the task pipeline
extract >> transform >> load

# Submit the DAG
cp process_web_log.py $AIRFLOW_HOME/dags

# Unpause the DAG
airflow dags unpause process_web_log
```
