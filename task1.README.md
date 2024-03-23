## 1.What is OLTP and OLAP
**OLTP**: Online Transaction Processing (OLTP) enables the real-time execution of large numbers of database transactions by large numbers of people, typically over the internet. A database transaction is a change, insertion, deletion, or query of data in a database. it is a type of database system that is used for high-speed data processing and rapid transaction execution in real-time. Businesses use OLTP systems to manage a large volume of database transactions from many users without harming database consistency and accuracy.A database transaction is any change made in a database, like inserting or deleting. OLTP databases are relational databases. They organize data in tables consisting of rows and columns.

**OLTP Architecture**: It has 3 layers The presentation layer:
This layer is the front end or user interface where transactions are generated. The logic layer: Also called the business logic or application layer, this layer processes transaction data based on predefined rules. The data or data store layer: This is where each transaction and related data are stored and indexed. It includes the database management system (DBMS) and the database server.

Each layer has its own infrastructure and updating intervals. They operate independently so that changes to one layer do not impact the others.

**Characterstics of OLTP**:

* fast query processing: OLTP systems are used for high-speed query processing. They handle transactions in real-time, meaning that transactions are executed as soon as they are received, with little or no delay.

* High concurrency :OLTP systems use algorithms that allow many concurrent users to perform transactions simultaneously. Each transaction is executed independently of the others and in the proper order. Two users cannot change the same data within an OLTP database at the same time, which is crucial for maintaining data integrity.

* supports ACID properties

Atomicity: Transactions in OLTP systems are atomic, meaning they are treated as a single, indivisible unit of work. If any part of a transaction fails, the entire transaction is rolled back, so the database is left in its original state.

Consistency: OLTP databases are designed to maintain data consistency, despite failures or errors. Every transaction changes tables in predefined and predictable ways, and the database will always be in a valid state.

Isolation: Transactions in OLTP systems are isolated from each other. This means that when multiple users read and write data simultaneously, they are executed independently. Isolation ensures that the changes made by one transaction do not interfere with the changes made by others. It keeps the database in a consistent state.‍

Durability: When a transaction is successfully executed in an OLTP database, the changes to the data are permanent and will survive any subsequent failures or errors, like system crashes or power outages.

* Support for simple transactions: OLTP systems support specific applications or business processes like order processing, inventory management, or customer service. They are typically not used for complex queries, data analysis, or reporting tasks.
**Examples**: ATM machines and online banking applications, Credit card payment processing, Order entry,Online bookings, Record keeping (including health records, inventory control, production scheduling, claims processing, customer service ticketing, and many other applications)

**OLAP**: OLAP (online analytical processing) is a computing method that enables users to easily and selectively extract and query data in order to analyze it from different points of view.

**OLAP Architecture**: online analytical processing (OLAP) systems store multidimensional data by representing information in more than two dimensions, or categories. Two-dimensional data involves columns and rows, but multidimensional data has multiple characteristics

Usually OLAP systems consists of Data warehouse, ETL tools, OLAP server, OLAP database, OLAP cubes, OLAP analytic tools

**OLAP Working:**

An online analytical processing (OLAP) system works by collecting, organizing, aggregating, and analyzing data using the following steps:

The OLAP server collects data from multiple data sources, including relational databases and data warehouses. Then, the extract, transform, and load (ETL) tools clean, aggregate, precalculate, and store data in an OLAP cube according to the number of dimensions specified. Business analysts use OLAP tools to query and generate reports from the multidimensional data in the OLAP cube. OLAP uses Multidimensional Expressions (MDX) to query the OLAP cube. MDX is a query, like SQL, that provides a set of instructions for manipulating databases.

**Examples:** OLAP can be used for data mining or the discovery of previously undiscerned relationships between data items,


## 2.Differences between OLTP & OLAP

**The primary purpose:** OLAP is to analyze aggregated data, while the OLTP is to process database transactions.

**uses:** OLAP systems are used to generate reports, perform complex data analysis, and identify trends. OLTP systems are used to process orders, update inventory, and manage customer accounts.

**Data formatting:** OLAP systems use multidimensional data models, so you can view the same data from different angles. OLTP systems are unidimensional and focus on one data aspect. They use a relational database to organize data into tables.

**Data architecture:** OLAP prioritizes data read over data write operations. it can quickly and efficiently perform complex queries on large volumes of data. Availability is a low-priority concern as the primary use case is analytics. OLTP prioritizes data write operations. It’s optimized for write-heavy workloads and can update high-frequency, high-volume transactional data without compromising data integrity.

**Performance:** OLAP processing times can vary from minutes to hours depending on the type and volume of data being analyzed. To update an OLAP database, you periodically process data in large batches then upload the batch to the system all at once. Data update frequency also varies between systems, from daily to weekly or even monthly. OLTP processing time is in milliseconds or less. OLTP databases manage database updates in real time. Updates are fast, short, and triggered by you or your users.

**Example applications:** OLAP is good for analyzing trends, predicting customer behavior, and identifying profitability. OLTP is good for processing payments, customer data management, and order processing.


## 3.Database Normal forms(4 normal forms)
**Normalization** :  It is the process of determining how much redundancy exists in a table. The goals of normalization are to:
* Be able to characterize the level of redundancy in a relational schema
* Provide mechanisms for transforming schemas in order to remove redundancy
It eliminates repeated data.
It came into existance because of anamolies present in the data.

Data anamolies are insertions, Updatation and deletion

##### Normal Forms:
Total there are 6 normal forms. There are 4 most important normal forms. They are
* First normal form (1NF)
* Second normal form (2NF)
* Third normal form (3NF)
* Boyce-Codd normal form (BCNF)

**First Normal Form (1NF)**: table should satisfy atomicity property.In the first normal form, only single values are permitted at the intersection of each row and column; hence, there are no repeating groups.To normalize a relation that contains a repeating group, remove the repeating group and form two new relations.The PK of the new relation is a combination of the PK of the original relation plus an attribute from the newly created relation for unique identification

**Second Normal Form (2NF)**:For the second normal form, the relation must first be in 1NF and should not contain partial dependancy . The relation is automatically in 2NF if, and only if, the PK comprises a single attribute.If the relation has a composite PK, then each non-key attribute must be fully dependent on the entire PK and not on a subset of the PK (i.e., there must be no partial dependency or augmentation).

**Third Normal Form (3NF)**:To be in third normal form, the relation must be in second normal form. Also all transitive dependencies must be removed; a non-key attribute may not be functionally dependent on another non-key attribute.

**Boyce-Codd Normal Form (BCNF)**: When a table has more than one candidate key, anomalies may result even though the relation is in 3NF. Boyce-Codd normal form is a special case of 3NF. A relation is in BCNF if, and only if, every determinant is a candidate key.

## 4.Dimension VS Fact table
**Fact Table**:Fact table is a primary table in a dimensional model. A Fact table contains the quantifiable data for analysis — the numerical measures (often additive) of the business processes. The Fact table also has foreign keys which refer to candidate keys in the Dimension tables.
In a data warehouse, a fact table is a table that stores the measurements, metrics, or facts related to a business operation. 

It is located at the center of a star or snowflake schema and is surrounded by dimension tables.

When multiple fact tables are used, they can be organized using a "fact constellation schema." 

A fact table has two types of columns: those that contain the facts and those that serve as foreign keys linking to dimension tables. 

The primary key of a fact table is often a composite key made up of all of the foreign keys in the table. 

Fact tables can hold various types of measurements, such as additive, non-additive, and partly additive measures, and store important information in the data warehouse. 

They are useful for evaluating dimensional attributes because they provide additive values that can act as independent variables.

**Dimesion TAble**:Dimension table is a structure that categorizes facts and measures in order to enable users to answer business questions. Dimensions are descriptive and define the characteristics of a business object. They provide context to facts — as they hold the fields which are descriptive, qualitative and textua

 These tables are usually small, with a number of rows ranging from a few hundred to a few thousand. 
The term "dimension table" refers to a set of data related to any quantifiable event and is the foundation for dimensional modeling. 
Dimension tables have a column that serves as a primary key, allowing each dimension row or record to be uniquely identified. This key is used to link the dimension table to the fact tables. A surrogate key, which is a system-generated key, is often used to uniquely identify the rows in the dimension table.

## 5.Types of Dimensions
There are mainly 10 types of dimensions available 
* slowly changing dimensions
* junk dimensions
* Conformed dimensions
* Degenerated dimensions
* Rapidly changing dimensions
* Stacked dimensions
* Inferred dimensions
* Role Playing dimensions
* Shrunken dimensions
* Static dimensions

**Slowly Changing Dimensions (SCD)** - dimensions that change slowly over time, rather than changing on regular schedule, time-base. There are many approaches how to deal with SCD. The most popular are:

Type 1 - Overwriting the old value:

Type 2 - Creating a new additional record

Type 3 - Adding a new column

**Rapidly / Fast Changing Dimensions (FCD)** - if one or more of its attributes in the table changes very fast and in many rows. Consider patient dimension as an example to it. By separating the rapidly changing attributes from the slowly changing ones and move those attribute to another table called junk dimension and maintain the slowly changing attribute in same table. 
**Junk Dimensions** - is a convenient grouping of typically low-cardinality flags and indicators. By creating an abstract dimension as above splitting FCD into Junk, we remove the flags from the fact table while placing them into a useful dimensional framework. Eg: Stock Data
**Conformed Dimensions** are dimensions that are shared by multiple stars. its example would be Item, region or location, Datetime dimensions, i.e. both Inventory and sales department can use such dimension for their reporting purpose. Eg: Calendar data
**Degenerate Dimension** is when the dimension attribute is stored as part of fact table, and not in a separate dimension table. These are essentially dimension keys for which there are no other attributes. In a data warehouse, these are often used as the result of a drill through query to analyze the source of an aggregated number in a report. You can use these values to trace back to transactions in the OLTP system. For example, receipt number does not have dimension table associated with it. Such details are just for information purpose


## 6.Snowflake VS Star Schema
**Star Schema**: Star schema is the simplest method for arranging data in a data warehouse. It contains a fact table at the center connected to dimension tables around it. Star schema is most effective for quick and simple data query execution. 

**Snowflake Schema**: Snowflake schema is a more complex method of storing data in which fact tables, dimension tables and sub-dimension tables are connected through foreign keys. Snowflake is most effective for in-depth data query analyses.

* Both fact tables and dimension tables are present in a star schema.Dimension tables,  sub-dimension tables, and fact tables are all included in a snowflake schema.
* Type of Model: The star schema is a top-down type of model.The snowflake schema is a bottom-up type of model.
* Space:Star schema uses more space compared to Snowflake Schema.Snowflake schema uses less space comparatively.
* Joint Relations: In a star schema, relationships between tables are represented by a single join, resulting in a simple data structure for fast query performance and easy data analysis.The snowflake schema has a complex data structure with multiple levels of relationships between tables, represented by multiple joins. This can make the data structure more difficult to understand and result in slower query performance.
* Response Time for Queries:Star schemas have faster query execution times due to a single join of a fact table and its attributes in dimensional tables.Snowflake schemas require complex joins between tables, which can slow down query processing and impact other OLAP products.
* Normalization: In a star schema, dimension tables are not organized in a normalized form. They are typically denormalized and contain multiple levels of information about a particular subject in a single table.Dimension tables in snowflake schema are normalized.
* Design Complexity: Star schema has simpler design
* Query Complexity: Star schemas have simpler query design due to the fact the table is joined to only one level of dimensional tables.Snowflake schemas, on another hand, have a more complex query design due to the need for multiple joins between the fact table and its dimensional tables. This leads to additional overhead in query writing.
* Foreign Keys: Have a lesser number of foreign keys.Comparatively has more foreign keys.
* Data Redundancy:The star schema stores redundant data in the dimension tables.The snowflake design fully normalizes the dimension tables and prevents data redundancy,
