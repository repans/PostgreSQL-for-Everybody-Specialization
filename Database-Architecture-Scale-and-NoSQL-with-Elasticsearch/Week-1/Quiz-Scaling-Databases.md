```
  # Do not copy if you are taking the test.
  # According to Coursera Honor Code,
  # Submitting work that isn’t your own may result in permanent failure of your running course or  
  # deactivation of your Coursera account.
```
--- 

# [Scaling Databases](https://www.coursera.org/learn/database-architecture-scale-nosql-elasticsearch-postgresql/exam/BlD7f/scaling-databases/)

### 01. What is the primary difference between ACID and BASE databases?
- [ ] The ability to store schemaless data in JSON
- [ ] The ability to replicate data to increase read performance
- [x] The view that multiple simultaneous readers have on the data
- [ ] The performance of re-indexing operations


### 02. What concept in relational database design is generally ignored in BASE database systems?
- [ ] Never store JSON data uncompressed 
- [ ] Use B-tree indexes below a certain number of rows
- [x] Don't allow vertical replication of string data
- [ ] Name tables using plural names and objects with singular names


### 03. Why is the term "NoSQL" used less and less recently?
- [x] Many BASE-style databases are providing SQL interfaces
- [ ] Because NoSQL has "won" and SQL is no longer in common use
- [ ] Oracle trademarked NoSQL(tm) and no one wanted to pay a license fee
- [ ] Because brands like Mongo and Cassandra became well known


### 04. Of the "letters" in the BASE abbreviation, which captures the notion best?
- [ ] Big Data
- [ ] Atomicity
- [ ] Soft limits
- [x] Eventual Consistency


### 05. Which of the following techniques has a negative performance impact (and is usually not supported) in a BASE-style database?
- [-] Schema-on-read 
- [ ] SERIAL primary keys
- [ ] Extending the schema on the fly
- [ ] GUID primary keys


### 06. Which of the following techniques used to scale ACID-style databases is in a sense BASE-like?
- [ ] Read replicas
- [ ] Multi-Master
- [ ] SSD
- [ ] Each tenant has its own database instance
- [-] Vertical scaling


### 07. Which of these database architectures came first?
- [ ] BASE
- [-] ACID
- [ ] Its complicated


### 08. Which of the following does NOT belong for a BASE-style database system:
- [ ] It is easy to have an unique integer key that increments for each row and is provided by the database
- [ ] Data is distributed on many servers and requests can go to any server
- [ ] A service can be scaled horizontally by adding more servers
- [-] Data is often sharded 


### 09. Which of these techniques is a critical element of a single-instance BLOB storage approach?
- [ ] Alpha-Beta pruning
- [ ] Hashing
- [ ] Dictionaries
- [-] Garbage collection



--- 
> [Database Architecture, Scale, and NoSQL with Elasticsearch](https://www.coursera.org/learn/database-architecture-scale-nosql-elasticsearch-postgresql/) {[Week-1](https://www.coursera.org/learn/database-architecture-scale-nosql-elasticsearch-postgresql/home/week/1)}
