# Cloud Architectures
##### Graded Quiz • 30 min • 9 total points available 
---
Graded-Quiz--Cloud-Architectures.md
### Q1: Why is the term "NoSQL" used less and less recently?

- [ ] Oracle trademarked NoSQL(tm) and no one wanted to pay a license fee
- [x] Many BASE-style databases are providing SQL interfaces
- [ ] Because brands like Mongo and Cassandra became well known
- [ ] Because NoSQL has "won" and SQL is no longer in common use


### Q2: Why are the database requirements for Facebook so much more complex than those for GMail?

- [ ] Facebook needs to handle lots of photos
- [x] Facebook needs to distribute data across many data centers around the world
- [ ] Facebook must handle friends and privacy
- [ ] Facebook stores far more data than GMail


### Q3: What kind of computers would you see in a Google data center?

- [ ] Simple commodity computers without any extra packaging
- [x] Rows and rows of rack-mounted specialized hardware
- [ ] Multi-processor systems connected to large RAID disk arrays
- [ ] Large refrigerator-sized computers with 100's of CPUs and large shared memory


### Q4: How many computers are involved in producing a Google search result?

- [ ] 1
- [ ] 5000
- [ ] 10
- [x] 200


### Q5: What is the first step in a Google search to get to the point where you see the top pages on the Internet that match your search?

- [x] Inverted index of keywords
- [ ] Quality measure of the website content
- [ ] Page rank
- [ ] The supplemental index


### Q6: How did/does Amazon Web Services "encourage" application architects to build distributed applications?

- [ ] Disk space was more expensive than main memory
- [x] Software as a service (like Redshift) was far less expensive than building your own database servers
- [ ] Temporary disk space was cheaper than permanent space
- [x] Small memory systems are the most cost effective


### Q7: Which of the following does NOT belong for a BASE-style database system:

- [x] It is easy to have a unique integer key that increments for each row and is provided by the database
- [ ] Data is distributed on many servers and requests can go to any server
- [ ] A service can be scaled horizontally by adding more servers
- [ ] Data is often sharded


### Q8: What database was used to develop Amazon's RedShift service?

- [ ] MySQL
- [ ] MongoDB
- [ ] Cassandra
- [x] PostgreSQL
- [ ] Oracle


### Q9: How have traditional ACID database vendors like PostgreSQL reacted to the rise in popularity of new NoSQL / BASE database systems?

- [x] By adding optional NoSQL / BASE features like JSON fields and read replicas
- [ ] By evolving the SQL language to be SQL++
- [ ] By pointing out that BASE databases are eventually consistent
- [ ] By removing support for transactions and SERIAL fields to improve performance


--- 
> [Database Architecture, Scale, and NoSQL with Elasticsearch](https://www.coursera.org/learn/database-architecture-scale-nosql-elasticsearch-postgresql/) {[Week-2](https://www.coursera.org/learn/database-architecture-scale-nosql-elasticsearch-postgresql/home/week/2)}
