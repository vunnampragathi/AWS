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
##### Normal Forms:
Total there are 6 normal forms. There are 4 most important normal forms. They are
* First normal form (1NF)
* Second normal form (2NF)
* Third normal form (3NF)
* Boyce-Codd normal form (BCNF)

**First Normal Form (1NF)**: In the first normal form, only single values are permitted at the intersection of each row and column; hence, there are no repeating groups.To normalize a relation that contains a repeating group, remove the repeating group and form two new relations.The PK of the new relation is a combination of the PK of the original relation plus an attribute from the newly created relation for unique identification

**Second Normal Form (2NF)**:For the second normal form, the relation must first be in 1NF. The relation is automatically in 2NF if, and only if, the PK comprises a single attribute.If the relation has a composite PK, then each non-key attribute must be fully dependent on the entire PK and not on a subset of the PK (i.e., there must be no partial dependency or augmentation).

**Third Normal Form (3NF)**:To be in third normal form, the relation must be in second normal form. Also all transitive dependencies must be removed; a non-key attribute may not be functionally dependent on another non-key attribute.

**Boyce-Codd Normal Form (BCNF)**: When a table has more than one candidate key, anomalies may result even though the relation is in 3NF. Boyce-Codd normal form is a special case of 3NF. A relation is in BCNF if, and only if, every determinant is a candidate key.

## 4.Dimension VS Fact table


## 5.Types of Dimensions


## 6.Snowflake VS Star Schema
