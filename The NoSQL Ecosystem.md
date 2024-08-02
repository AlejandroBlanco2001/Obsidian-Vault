Keywords: #databases #nosql 
Topic: [[Databases]]


In this topic, the discussion is around the whole NoSQL ecosystem, taking into account the types and use cases.
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
>Most of the work (or a long part) is the *query optimizer* [[Query Optimizer]] that is a structure that enables the DBMS to make changes in the original query to have a better performance. (I should read about this a little bit more)
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

## Data Models 

### Complex queries

- MongoDB allows you to index your data based on any number of properties and has a relatively high-level language for specifying which data you want to retrieve.

- BigTable-based systems support scanners to iterate over a column family and select particular items by a filter on a column.

- CouchDB allows you to create different views of the data, and to run MapReduce tasks across your table to facilitate more complex lookups and updates

### Transactions

- In the NoSQL world you prefer performance over *transactional semantics*, 
- The SQL database will offer ACID guarantees between transactions.
	- This makes us as developers sane about how the data is stored and healthy.
	- This safety cost us performance 
- NoSQL is fast and leave all this to developer in some cases 
- Nowadays, some databases offer some safe guards to this, for example Redis, provides the `MULTI` command to allow a series of queries to be made.

### Schema-free storage

-  The NoSQL databases are schema-free, this is wonderful tool for not structure data, but after this can cause also more issues that need it.
	- What if the record doesn't have certain property? Error? Handle the error?
	- What if the schema is updated partially?
	- The developer MUST program in the most defensive way possible 

# Data durability

- Ideally, all data modifications on a storage system would immediately be safely persisted and replicated to multiple locations to avoid data loss.

- However, ensuring data safety is in tension with performance, and different NoSQL systems make different _data durability_ guarantees in order to improve performance. 

- Failure scenarios are varied and numerous, and not all NoSQL systems protect you against these issues.

### Single-server Durability

The simplest form of durability is a _single-server durability_, which ensures that any data modification will survive a server restart or power loss.

-Ideally, you want a system to minimize the number of writes between `fsync` calls, maximizing the number of those writes that are sequential, all the while never telling the user their data has been successfully written to disk until that write has been `fsync`ed

#### Control fsync Frequency

- Memcached s an example of a system which offers no on-disk durability in exchange for extremely fast in-memory operations. When a server restarts, the data on that server is gone: this makes for a good cache and a poor durable data store.

- Redis offers developers several options for when to call `fsync`. Developers can force an `fsync` call after every update, which is the slow and safe choice

#### Increase Sequential Writes by Logging

- Several data structures, such as B+Trees, help NoSQL systems quickly retrieve data from disk. Updates to those structures result in updates in random locations in the data structures' files, resulting in several random writes per update if you `fsync` after each update.

- To reduce random writes, systems such as Cassandra, HBase, Redis, and Riak append update operations to a sequentially-written file called a _log_.

- By treating the log as the ground-truth state of the database after a crash, these storage engines are able to turn random updates into sequential ones

- While NoSQL systems such as MongoDB perform writes in-place in their data structures

#### Increase Throughput by Grouping Writes

- Cassandra groups multiple concurrent updates within a short window into a single `fsync` call. This design, called _group commit_, results in higher latency per update, as users have to wait on several concurrent updates to have their own update be acknowledged

### Multi-server Durability

Because hard drives and machines often irreparably fail, copying important data across machines is necessary. Many NoSQL systems offer multi-server durability for data.

- Redis takes a traditional master-slave approach to replicating data. 
	- All operations executed against a master are communicated in a log-like fashion to slave machines, which replicate the operations on their own hardware. If a master fails, a slave can step in and serve the data from the state of the operation log that it received from the master
	
	- CouchDB facilitates a similar form of directional replication, where servers can be configured to replicate changes to documents on other stores

- MongoDB provides the notion of replica sets, where some number of servers are responsible for storing each document. MongoDB gives developers the option of ensuring that all replicas have received updates, or to proceed without ensuring that replicas have the most recent data.

# Scaling for Performance

- You load the data correctly, the data gets in memory, is a big piece of data, therefore, you PC start failing, solutions?
	- Increase the server power (Memory and Space)
	- But what happens if you scale and scale, and it's to expensive?
	- You will need more PCs, and distribute the load and the data

That approach is called 'scale out', and is measure by the 'horizontal scalability']

>[!NOTE]
>The ideal horizontal scalability goal is _linear scalability_, in which doubling the number of machines in your storage system doubles the query capacity of the system.

To be able to do this, you must do `Sharding`

>[!NOTE]
>Is the act of splitting your read and write workload across multiple machines to scale out your storage system. Also means that no one machine has to handle the write workload on the entire dataset, but no one machine can answer queries about the entire dataset.

>[!IMPORANT]
>Sharding is hard, sharding is complex, don't do sharding unless that is the last resource

## How to avoid sharding

### Read replicas

Many storage systems see more read requests than write requests. A simple solution in these cases is to make copies of the data on multiple machines. All write requests still go to a master node. Read requests go to machines which replicate the data, and are often slightly stale with respect to the data on the write master.

### Caching

Caching the most popular content in your system often works surprisingly well. Memcached dedicates blocks of memory on multiple servers to cache data from your data store. Memcached clients take advantage of several horizontal scalability tricks to distribute load across Memcached installations on different servers. To add memory to the cache pool, just add another Memcached host.

## Sharding

### Coordinators

The CouchDB project focuses on the single-server experience. Two projects, Lounge and BigCouch, facilitate sharding CouchDB workloads through an external proxy, which acts as a front end to standalone CouchDB instances. In this design, the standalone installations are not aware of each other. The coordinator distributes requests to individual CouchDB instances based on the key of the document being requested

### Consistent Hash Rings

- _distributed hash tables_ (_DHTs_) is a way of consistent hashing
-
![[Pasted image 20240802001246.png]]

To do this, we map all keys to a server by seeing if it falls in the range between that server and the next one in the ring. For example, `A` is responsible for keys whose hash value falls in the range [7,233], and `E` is responsible for keys in the range [875, 6] (this range wraps around on itself at 1000). So if `H('employee30') mod L = 899`, it will be stored by server `E`, and if `H('employee31') mod L = 234`, it will be stored on server `B`.

### Replicating Data

- Achieved multi-server durability through key-value replication across servers in a ring.
- Managed workload failover using neighbor servers or temporary replication.
- Implemented replication factor to ensure data availability during server failures.

### Achieving Better Distribution

- Addressed uneven load distribution in small server setups.
- Implemented virtual nodes to balance key distribution across physical machines.
- Applied load-balancing processes to adjust server positions based on historical load.

### Range Partitioning

- Used range partitioning to manage metadata and route key lookups to appropriate servers.
- Enabled fine-grained load management by adjusting key ranges on servers.
- Integrated additional architectural components for monitoring and routing shards.

### BigTable-Based Range Partitioning

- Developed a hierarchical sharding technique storing key ranges within tablets.
- Adjusted tablet size and server assignments dynamically based on load.
- Utilized a three-layer hierarchy for efficient key lookup and reduced metadata load.

## Handling Failures

- Designed systems to manage master and tablet server failures with minimal impact.
- Employed distributed locking systems like Chubby and ZooKeeper for server membership and liveness management.
- Ensured continuous operation through automated tablet re-assignment.

### Range Partitioning-Based NoSQL Projects

- Integrated BigTable's hierarchical range-partitioning approach in HBase, MongoDB, and Cassandra.
- Managed data replication and consistency using distributed file systems and replica sets.
- Implemented order-preserving partitioners for efficient range scans.

### Consistency

- Balanced strong consistency and eventual consistency based on use-case requirements.
- Applied the CAP theorem to manage consistency, availability, and partition tolerance in distributed systems.
- Designed systems for achieving strong consistency through write and read quorum requirements.

### Eventual Consistency

- Used vector clocks for data versioning and conflict detection.
- Implemented conflict resolution strategies, including application-level merging and timestamp-based resolution.
- Employed read repair and hinted handoff techniques to handle temporary unavailability and improve synchronization.
- Utilized anti-entropy processes like Merkle Trees for efficient replica synchronization.
- Adopted gossip protocols to monitor and manage node health in distributed systems.