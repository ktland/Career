# Intro to SQL (Structured Query Language)

## Intro to the Database Concept

### What is a Database?

- A database is a collection of integrated data or records
  - term “database” can refer to any collection of data items
  - a “record” is a representation of a physical or conceptual entity
- A database consists of both data and metadata
  - metadata is information that describes the data structure inside the database
  - database stores metadata in a data dictionary that describes the columns, tables, and indexes
- Database contains a description of its own structure
  - integrating both data and the relationship among them

### Databases in More Detail

- Databases come in a variety of sizes
  - as simple as standard collection of phone numbers
  - as complex as commercial-grade systems holding millions of records
- Personal database is designed for single users on a single computer
  - simple structure and small in size
- Public workgroup databases are designed for commercial use or a workgroup within an organization
  - larger than a personal database and capable of handing a group of users accessing the same data at the same time
- Enterprise databases are designed for several hundred groups of users
  - model the flow of an entire organization

### What is Database Management?

- Databases are usually associated with software, allowing the data to be managed or queried
  - SQL Server
  - Microsoft Access
  - IBM DB2
  - MySQL
  - Oracle
- A Database Management System (DBMS) is a set of programs used to provision databases and their associated applications and processes

### What is a Flat File System?

- Flat files
  - provide minimal structure
  - collection of one data record after another, in an organized format
  - a list containing nothing but data
  - each field in the list has a fixed length
  - low overhead provides quicker response times and associated smaller systems
    - does *not* scale well
  - migrating a flat file system takes much more time than a DBMS system

### Relevance of Databases and SQL

- Databases allow you to set up rules to keep data consistent and fault-tolerant
  - organize data to retrieve upon command
  - enable you to break the data into parts
- SQL is used to communicate with the database
  - language standard for management of relational databases referenced by ANSI
- Without communication to the database, the user would not be able to perform controlled tasks to update, retrieve, and manage the data

## The Relation of Data and the Various Databases

### Different Models

| Hierarchical Database  | Relational Database | Network Database |
|:--|:--|:--|
| Data retrieval architecture in relation to hierarchy | Always the primary choice for non-legacy systems and used for relational models | Databases over a network and provide minimal redundancy |

### The Relational Model

- All data is represented by tuples and grouped into relations
  - a database managed in terms of the relational architecture is a relational database
- Primary model used around the world for data storage and processing
- Relational databases offer flexibility, are easier to maintain
  - structures that follow the hierarchical or network architecture have that structure hard-coded into the application
  - relational databases store data in tables that are largely independent of each other except for the relationship between them

### Components of a Relational Model

- Tuple
  - single row of a table that contains a single record for that relation
- Tables
  - relations are saved in table format
  - collection of all records for that relation
- Relation Schema
  - schema describes the relation identity and attributes
  - attributes = columns
- Relation Key
  - each attribute of a row is called a relation key
  - identifies the row in the relation
- Relation Instance
  - specific set of tuples in a relational database architecture
  - instances with unique tuples

### Why Relational Databases Are Effective

- Compatibilities catering to future requirements
  - effective for records that may not be added until later
- Use of complex queries to carry out large-scale tasks
  - use of the Structured Query Language
- Managed Security
  - implementations in a custom level and cater to the individual’s needs
- Data is added once and remains in the system
  - changes are made and applied once
- Data is easily accessed and managed

## Dissecting the Code behind Structured Query Language

### What is SQL Code?

- Normally a non-procedural programming language
  - simply tell SQL what you want by creating a set of queries and execute it instead of telling the system how you want to get what you want
  - by using the object-oriented functionalities in SQL, you can create procedural queries
- DBMS decides the best way to get what you requested
- Query
  - a question you ask the database
  - if any of the data in the database complies with the conditions of the query, SQL retrieves the data

### SQL Extracting Information

- Two ways to extract information from a database:
  - (administrator) create an ad hoc query from a console by typing the queries and reading the results from the display
  - (end user) execute an application that collects information from the database and reports on the information on-screen or in a printed report

```SQL
CREATE PROCEDURE CustOrders @CustomerID
nchar(5)
AS
BEGIN
	--comments
	SELECT
		OrderID,
		OrderDate,
		RequiredDate,
		ShippedDate
	FROM
		Orders
	WHERE
		CustomerID = @CustomerID
	 ORDER BY
	 	 OrderID
END
```

### Basics of SQL Commands

- SQL has three main roles:
  - querying a database to retrieve the necessary data
  - creating a database and defining its structure
  - controlling data security
- SQL sub-language called Data Manipulation Language (DML) works with queries and data manipulation

### Why are Queries Used?

- Provide the user a snapshot of the data contents
  - executing a simple query can provide the details of required data upon request and executes on command

## Intro to the SQL Syntax

```SQL
/*
SELECT → list of columns
FROM → name of table(s)
WHERE → enter criteria
ORDER BY → specify sorted column(s) and sort order (ASC/DESC)
GROUP BY → enter column(s) to categorize results
HAVING → enter criteria for the grouped column(s)
*/

--Basic Select Statement Syntax
Select * From Customers

--A filtered Select Statement to retrieve only specific records from a table
Select CustomerID, CompanyName, Country from Customers --Each column name must be seperated by a comma
Where Country = 'Germany' or Country = 'USA'
Order By CompanyName; --Defaults to ascending
Go
```

## Understanding Data Types

### Various Data Types

- Numerics
- Booleans
- Intervals
- Chronological
- Strings

### Numerical Data Types

| Data Type | Description | Precision Type (bytes) |
|:----------|:------------|:-----------------------|
|**BIGINT**     |No decimal <br> (-9,223,372,036,854,775,807 to 9,223,372,036,854,775,807)|8(2^64)
|**INT**        |No decimal <br> (-2,147,483,647 to 2,147,483,647)|4(2^32)|
|**SMALLINT**   |No decimal <br> (-32768 to 32767)| 2(2^16)|
|**TINYINT**    |No decimal <br> (0 to 255)|1(2^8)|

### Exact and Approximate Numerical Data Types

|Data Type|Description|Precision Type|
|:--------|:----------|:-------------|
|**REAL**|Data of approximate numerical value|7|
|**FLOAT**|Data of approximate numerical value|16|
|**FLOATp**|Data of approximate numerical value|p|
|**DECIMALp**|Data of exact numerical value|p|
|**NUMERICp**|Data of exact numerical value|p|

### Boolean and String Data Types

|Data Type|Description|
|:--|:--|
|**Boolean**|Stores either true or false value|
|**BINARY**|Data of binary string value fixed-length|
|**VARCHAR**|Data of character string value variable length|
|**CHARACTER**|Data of character string value fixed-length|
|**VARBINARY**|Data of binary string value variable length|

### Chronological and Interval Data Types

|Data Type|Description|
|:--|:--|
|**INTERVAL**|Ranges from a number of integer fields, can represent a period of time (all depends on the interval type)|
|**DATE**|Stores day, year, month data values|
|**TIME**|Stores seconds, minutes, hours data values|
|**TIMESTAMP**|Stores the complete date from year, month, day, hour, minute, and second data values|

## Ready to Create A Database

- Logical Name
  - database files
  - everything that you store in the database is ultimately stored within a file

### Creating A Database via Code

```sql
CREATE DATABASE My_TestDB
ON PRIMARY
(NAME = 'My_TestDB', FILENAME = 'C:\Databases\My_TestDB.mdf', SIZE = 5120KB, FILEGROWTH = 2048KB)
LOG ON
(NAME = 'My_TestDB', FILENAME = 'C:\Databases\My_TestDB.ldf', SIZE = 2048KB, FILEGROWTH = 20%)
GO
```

## How to Create A Table

- A table is a two-dimensional array consisting of rows and columns
  - similar to an Excel spreadsheet
  - create a table using the `SQL CREATE TABLE` command
    - parameters include the name and data type of each column
  - use the `ALTER TABLE` command to change the structure of the table
  - `DROP` command can delete the table upon request

### Table Creation Syntax Example

```sql
CREATE TABLE CUSTOMER
(
  CustomerID INTEGER    NOT NULL,
  FirstName  VarCHAR (15), --number in parentheses indicates highest number of characters allowed
  LastName   VarCHAR (20)  NOT NULL,
  Street     VarCHAR (25),
  City       VarCHAR (20),
  State      CHAR (2),
  Zipcode    INTEGER,
  Phone      CHAR (13)
)
```

### Key Points to Keep in Mind when Creating Tables

- Ensure that every table in the database has at least *one* common column
  - example: using the `CustomerID` column in another table called `Orders`
  - this helps to relate one table to another with a *common identifier*
- Identify all tables that will be used before creating them
- Define the columns that each table will need
- Give each table a primary key
  - example: using the `CustomerID` column as a primary key
- Refine each table to third normal form (3NF)
  - ***RESEARCH THIRD NORMAL FORM***

### Single and Multi-table Views

- Single-table view
  - useful when information exists in a single table
  - example would be list of names and phone numbers of persons from one city

```sql
CREATE VIEW CITYNAME_CUST AS
  SELECT CUSTOMER.FirstName,
       CUSTOMER.LastName,
     CUSTOMER.Phone
     FROM CUSTOMER
     WHERE CUSTOMER.City = 'CITYNAME'
```

- Multi-table View
  - this requires more than one table and is useful when requiring relation between tables and retrieving information from tables that have commonalities

|CUSTOMER TABLE|CityName_CUST View|
|:-------------|:-----------------|
|CustomerID    |                  |
|FirstName    →|FirstName         |
|LastName     →|LastName          |
|Street        |                  |
|City         →|City              |
|State         |                  |
|Zipcode       |                  |
|Phone        →|Phone             |

## Tables by Example

```sql
USE My_TestDB
GO

CREATE TABLE Test_Table_1
(
    Col1 int NOT NULL, --NOT NULL = can't be left blank
    Col2 varchar(10)
)
GO
```

## Adding Data Using INSERT Statement

```sql
--Verify records
Select * from Test_Table_1


--Insert values into explicit columns
INSERT INTO Test_Table_1 (Col1, Col2)
Values
(1, 'Hello')


--Insert values by position
INSERT INTO Test_Table_1
Values
(2, 'Hi')


--Insert multiple records at once
INSERT INTO Test_Table_1
Values
(3, 'Hey'),
(4, 'Hi there')
```

## Creating More Complex Tables

```sql
CREATE TABLE Customers
(
  CustomerID int NOT NULL,
  FirstName varchar(20) NOT NULL,
  LastName varchar(30) NOT NULL,
  Street varchar(15) NULL, --NULL is default and it isn't necessary to specify
  City varchar(15) NULL,
  State_Prov char(2),
  PostalCode varchar(10) NULL,
  Country varchar(20) NULL,
  Phone varchar(15) NULL,

--CONSTRAINT restricts the data that can be entered into any given column and disallows any duplication
  CONSTRAINT PK_Customers PRIMARY KEY CLUSTERED (CustomerID)
)
```

- `CONSTRAINT` → restricts the data that can be entered into any given column and disallows any duplication
- `PK_Customers` → name of the `CONSTRAINT`
- `PRIMARY KEY` → type of constraint
- `CLUSTERED` → indexed order of the values physically sorted by the `CustomerID` value
- `(CustomerID)` → the field in which the constraint is being placed

## Changing an Existing Table

```sql
--Use Alter Table to add a new column
ALTER TABLE Customers ADD
    MobilePhone varchar(15) NULL

--Use Alter Table to remove a column
ALTER TABLE Customers
    DROP COLUMN MobilePhone

--Use Alter Table to remove the primary key constraint
ALTER TABLE Customers
    DROP CONSTRAINT PK_Customers
```

## Deleting an Existing Table

```sql
DROP TABLE Test_Table_1
```

***BE CAREFUL!***

## Quick Peek Using SELECT Statement

```sql
--Script for SelectTopNRows command from SSMS (SQL Server Management Studio)
SELECT TOP 1000 [CustomerID]
      ,[CompanyName]
      ,[ContactName]
      ,[ContactTitle]
      ,[Address]
      ,[City]
      ,[Region]
      ,[PostalCode]
      ,[Country]
      ,[Phone]
      ,[Fax]
FROM [northwind] [dbo] [Customers]
```

## Learning the NULL Statement

```sql
--Select all records
Select * from Customers

--Find those with null values for the Region
Select CustomerID, City, Region
From Customers
Where Region IS NULL
```
