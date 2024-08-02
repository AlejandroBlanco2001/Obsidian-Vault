In this topic, the discussion is around the whole NoSQL ecosystem, taking intou account the types and use cases.

# Context

The NoSQL from a query interface that is no SQL if we read it just once and without much context. But, if you explore the whole environment you can find that is more ***Not Only SQL***, this propose a new way of thinking, you can **replace** or **mix**  your current SQL database. 

## What is SQL

SQL stands for *Structured Query Language* an this run on relational databases, that are based on entity-relation models. This is a declarative language for querying data.

>[!INFO]
>Declarative means that you tell the system what needs to do, and not how to do it.

For example if you have the following query 

```
Find the record for employee 39, project out only the employee name and phone number from their entire record, filter employee records to those that work in accounting, count the employees in each department, or join the data from the employees table with the managers table
```

This query tells what you need, but you don't have to worry about:
- How the data is stored in the disk
- Which indices you need to match
- Which algorithm use to process the data

>[!INFO]
>Most of the work (or a long part) is the *query optimizer* that is a structure that enables the DBMS to make changes in the original query to have a better performance. (I should read about this a little bit more)
>

The relational databases are great for the majority of uses cases where relations (duh) are need it, but they come with a complexity:

1. Complexity leads to unpredictability. SQL's expressiveness makes it challenging to reason about the cost of each query, and thus the cost of a workload.

2. There are many ways to model a problem and the relational data model is strict: the schema assigned to each table specifies the data in each row. If we are storing less structured data, or rows with more variance in the columns they store, the relational model may be needlessly restrictive.

 3. If the data grows past the capacity of one server, then the tables in the database will have to be partitioned across computers. To avoid JOINs having to cross the network in order to get data in different tables, we will have to de-normalize it. Denormalization stores all of the data from different tables that one might want to look up at once in a single place. This makes our database look like a key-lookup storage system, leaving us wondering what other data models might better suit the data.

## Inspiration for NoSQL

- Google's BigTable: Presents an interesting data model, which facilitates sorted storage of multi-column historical data. Data is distributed to multiple servers using a hierarchical range-based partitioning scheme, and data is updated with strict consistency. Further read [here](https://aosabook.org/en/v1/bib1.html#bib:bigtable)

- Amazon's Dynamo: Uses a different key-oriented distributed datastore. Dynamo's data model is simpler, mapping keys to application-specific blobs of data. The partitioning model is more resilient to failure, but accomplishes that goal through a looser data consistency approach called eventual consistency. Further read [here](https://aosabook.org/en/v1/bib1.html#bib:amazon:dynamo)

### Characteristics and Considerations

- The philosophy of the NoSQL can be reduce to: 'Simplifying how a database operates over data, an architect can better predict the performance of a query'

- The SQL ensure an ACID behavior, this means:
	- One operation at the time, Atomic
	- The next subqueries will have the updated value, Consistency
	- One change don't affect the other change, Isolated
	- Once the value is updated, it will persist, Durable
- NoSQL don't do that, and thus, is easier to partition data across machines

This is a set of considerations, if you want to use NoSQL

- _Data and query model_: Is your data represented as rows, objects, data structures, or documents? Can you ask the database to calculate aggregates over multiple records?

- _Durability_: When you change a value, does it immediately go to stable storage? Does it get stored on multiple machines in case one crashes?

- _Scalability_: Does your data fit on a single server? Do the amount of reads and writes require multiple disks to handle the workload?

- _Partitioning_: For scalability, availability, or durability reasons, does the data need to live on multiple servers? How do you know which record is on which server?

- _Consistency_: If you've partitioned and replicated your records across multiple servers, how do the servers coordinate when a record changes?

- _Transactional semantics_: When you run a series of operations, some databases allow you to wrap them in a transaction, which provides some subset of ACID (Atomicity, Consistency, Isolation, and Durability) guarantees on the transaction and all others currently running. Does your business logic require these guarantees, which often come with performance tradeoffs?

- _Single-server performance_: If you want to safely store data on disk, what on-disk data structures are best-geared toward read-heavy or write-heavy workloads? Is writing to disk your bottleneck?

- _Analytical workloads_: We're going to pay a lot of attention to lookup-heavy workloads of the kind you need to run a responsive user-focused web application. In many cases, you will want to build dataset-sized reports, aggregating statistics across multiple users for example. Does your use-case and toolchain require such functionality?

All of these are important, but the last three are crucial.

# Data and Query models

- Data model is how the data is represented and logically organized
- Query models is how to retrieve and update the data

## Key-based

We select a key to lookup and identify the data, and that's our filter.

In key lookup-based systems, complex join operations or multiple-key retrieval of the same data might require creative uses of key names. A programmer wishing to look up an employee by his employee ID and to look up all employees in a department might create two key types. For example, the key `employee:30` would point to an employee record for employee ID 30, and `employee_departments:20` might contain a list of all employees in department 20. A join operation gets pushed into application logic: to retrieve employees in department 20, an application first retrieves a list of employee IDs from key `employee_departments:20`, and then loops over key lookups for each `employee:ID` in the employee list.
### Key-Value

- Simplest form of Key-based
- Each key, points to some particular data (for example, a JSON)
- Easy query model
- Limited used cases 
- Voldemort is an example
### Key-Data

- Assign each value a type
- For example, you can have: integer, string, list, set, and sorted set.
- Now, you have what you will retrieve and not lose performance.
- Redis is an example

### Key-Document

- Assign a key to a document that have structured information
- Those documents are usually JSON
- Query logic is complex 
- MongoDB and CouchDB, are great examples

### BigTable Column Family Stores

- Assign a key to a row, which contains data stored in one or more Column Families (CFs)
- Within a CF, each row can contain multiple columns
- Each value is time-stamped
- Cassandra is a good example

## Graph storage

- They differ in all sense from the other NoSQL and SQL databases (data models, data traversal and querying patterns, physical layout of data on disk, distribution to multiple machines, and the transactional semantics of queries).
- Neo4J and HyperGraphDB are great examples

### Complex queries

- MongoDB allows you to index your data based on any number of properties and has a relatively high-level language for specifying which data you want to retrieve.

- BigTable-based systems support scanners to iterate over a column family and select particular items by a filter on a column.

- CouchDB allows you to create different views of the data, and to run MapReduce tasks across your table to facilitate more complex lookups and updates

### Transactions

- In the NoSQL world you prefer performance over *transactional semantics*.