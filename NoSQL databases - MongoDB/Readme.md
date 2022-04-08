# NoSQL databases - MongoDB

## Overview

In this assignment, an e-commerce company needed to design a data platform that used MongoDB as a NoSQL database to store catalog data. After importing the the data was necessary to create an indexe, make some queries and export selected fields from a collection into a csv file.

## Objectives

- import data into a MongoDB database
- query data in a MongoDB database
- export data from MongoDB


## Tools / Software

- MongoDB Server
- MongoDB Command Line Backup Tools
- Skills Network Labs Cloud IDE

### Download the catalog.json file
```
wget https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0321EN-SkillsNetwork/nosql/catalog.json
```

### Import 'catalog.json' into mongodb server into a database named 'catalog' and a collection named 'electronics'
```
mongo import -u root -p ***** --authenticationDatabase admin --db catalog -- collection electronics --file catalog.json
```

### List out all the databases
```
show dbs
```

### List out all the collections in the database catalog
```
use catalog;
show collections
```

### Create an index on the field "type"
```
db.electronics.createIndex({"type":1})
```

### Write a query to find the count of laptops
```
db.electronics.count( { type: "laptop" } )
```

### Write a query to find the number of mobile phones with screen size of 6 inches
```
db.electronics.count( {type: "smartphone" , 'screen size': 6 } )
```

### Write a query to find out the average screen size of smart phones
```
db.electronics.aggregate(
  [
    {
      $match:
        {
          type: "smart phone"
        }
    },
    {
      $group:
        {
          _id: "$type",
          average_screen_size: { $avg: "$screen size" }
        }
    }
  ]
)      
```

### Export the fields _id, "type", "model", from the 'electronics' collection into a file named electronics.csv
```
mongoexport -u root -p **** --authenticationDatabase admin --dbcatalog -- collection electronics --out electronics.csv -- type=csv --fields _id,type,model
```
