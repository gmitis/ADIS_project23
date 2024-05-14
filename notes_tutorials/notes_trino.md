# Backlog:
- discover trino deployment configurations [here](https://trino.io/docs/current/installation/deployment.html)
- check trino CLI commands 
- security, user file group rights -> Access control of CLI and security of cluster

---

# Presentation

## Trino and SQL

- runs SQL queries and returns results
- queries data wherever they may be
- excels on ad hoc analytics (on demand)
- fault toleraunt execution mode
- one query can run on all different data sources (SQL, MongoDB, etc) single point of access
- working with a cluster of workers
- What is SQL(declarative, relational model, data management/manipulation/analytics)
- data sources (what is, which is supported (rdbs, hadoop, nosql, etc))
- multiple databases but uses the same SQL queries no matter the database
- Trino handles OLAP (online analytical processing) workloads

## Generally

- Data lakes: Are like a big pile of raw materials
- Data warehouses: Are more organized and store data specifically for business intelligence
- iceberg data lake is very good with trino
- Starbust Galaxy: hands on improved SaaS version of Trino
- Iceberg data lake -> Trino: query-> result

## Catalog

what is a catalog:

- bunch of configuration pulled together and named that allows you to access a specific data source (represantation of underlying specific technology and how to access it)
- uses connector (read/write data in data source, translates Trino operations )
- contains specifications/ credentials
- trino queries a catalog which in turn queries that specific data source

## Trino Cluster

- one url
- many servers
- many catalogs
- many users/queries

## Clients

- what is use to run queries/ receive results
- can create a data pipeline/ report/ dashboard

## Summary

You can write a SQL query in a client, that is connected to a Trino cluster.

Trino retrieves data from the data sources with the help of the catalog configuration, and the connector that understands how to access data in the underlying data source.

## SQL Basics

-

---

# Documentation

## Architecture

- cluster: coordinator + many workers,
- coordinator:

  - connect to coordinator with client, orchestrates workload of workers

  * planning queries
  * managing nodes (workers)
  * client connects to coordinator
  * communication with REST API
  * logical model (stages) -> series of connected tasks -> run em in the cluster -> send back result to client

- worker:
  - run tasks
  - communicate with other workers
  - fetch data from connectors

## Data Sources

- connector:
  - system that can adapt Trino to a specific data source (eg: a DB )
  - contains several connectors
  - every catalog is assosiated with a connector (many to many)
- catalog:

  - contains schemas
  - references data source to a connector
  - catalog.schema.table (hive.test_data.test)

- schema:

  - set of tables of data

- table:
  - set of unordered rows organisez into named columns with types

# Query Execution Model

## Statement

- SQL statement to be executed
- further translation of statement and creation of a distributed query execution plan

## Query

- components (stages, tasks, connectors, splits etc) and configuration used to execute a statement given to Trino

## Stage

- breaked down parts to execute a distributed query
- tree of tasks
- arent executed on Trino workers
- series of tasks distributed over the cluster

## Task

- has input and output

## Split

- pieces of data that need to be processed by a specific task or given back to a higher up stage

## Driver

- one input and one output
- sequence of operator instances

## Operator

- An operator consumes, transforms and produces data

## Exchange

- exchange client
- tasks produce data which are stored on output buffers
- transfered data between nodes

---

# Installation

## Generally:

- can improve query fault tolerance
    - best suited for large batch queries
    - latency on short running queries
    - run dedicated fault tolerant cluster for batch operations

---
# Administration

webUI:


---



# Basic commands
Trino in Docker:
``` Dockerfile
# create and run container
docker run --name trino -d -p 8080:8080 -e CATALOG_MANAGEMENT=dynamic trinodb/trino     

# execute CLI
docker exec -it trino trino     
```
Start CLI in interactive mode: 
```bash 
./trino http://trino.example.com:8080

# basic query with JSON format for output
./trino --execute 'SELECT nationkey, name, regionkey FROM tpch.sf1.nation LIMIT 3' --output-format=JSON 

# --output-format=NULL: no output but if error displays error message
# ./trino --debug: view debug information
```   

---



