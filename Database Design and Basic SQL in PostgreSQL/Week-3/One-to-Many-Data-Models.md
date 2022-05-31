```
  # Do not copy if you are taking the test.
```
--- 

# One to Many Data Models


### 1. Primary keys are used to distinguish rows within in a table. 

____ [fill in blank] ______ keys are used to reference / point to a row with a primary key from a different table.

```
Foreign
```

### 2. Which of the following is NOT a good rule to follow when developing a database model?
- [x] Use a person's email address as their primary key
- [ ] Use integers as primary keys
- [ ] Model each "object" in the application as one or more tables
- [ ] Never repeat string data in more than one table in a data model

### 3. If our user interface (i.e., like iTunes) has repeated strings on one column of the UI, how should we model this properly in a database?
- [x] Make a table that maps the strings in the column to numbers and then use those numbers in the column
- [ ] Put the string in the first row where it occurs and then NULL in all of the other rows
- [ ] Put the string in the first row it occurs and then put that row number in the column all of the rest of the rows where the string occurs
- [ ] Encode the entire row as JSON and store it in a TEXT column in the database
- [ ] Put the string in the last row where it occurs and put the number of that row in the column all of the rest of the rows where the string occurs

### 4. Which of the following is the label we give a column that the "outside world" uses to look up a particular row?
- [x] Logical key
- [ ] Foreign key
- [ ] Primary key
- [ ] Local key
- [ ] Remote key
 
### 5. What is the label we give to a column that is an integer and is used to point to a row in a different table?
- [x] Foreign key
- [ ] Primary key
- [ ] Logical key
- [ ] Remote key
- [ ] Local key

### 6. What PostgreSQL keyword is added to primary keys in a CREATE TABLE statement to indicate that the database is to provide a value for the column when records are inserted?
- [ ] ASSERT_UNIQUE
- [ ] INSERT_AUTO_PROVIDE
- [ ] PRIMARY
- [x] SERIAL
- [ ] AUTO_INCREMENT

### 7. What is the SQL keyword that reconnects rows with foreign keys with the corresponding data in the table that the foreign key points to?
- [ ] APPEND
- [ ] CONSTRAINT
- [ ] CONNECT
- [x] JOIN
- [ ] COUNT

### 8. What does an "ON DELETE CASCADE" clause imply in a foreign key constraint in a PostgreSQL CREATE TABLE statement?
- [ ] Whenever a row is deleted, it is moved into a table named "CASCADE"
- [x] When a row in the parent table is deleted, all the rows in a child table that point to that row via a foreign key are deleted
- [ ] When rows in a child table are deleted, the primary key of the corresponding row in the parent table is set to NULL
- [ ] Whenever a row is deleted from the table, the other rows are scanned to insure that the logical key is unique and any duplicates are removed

### 9. What is the built-in PostgreSQL function that gives you the current time in an SQL statement?
- [ ] TODAY()
- [ ] DATE(false)
- [x] NOW()
- [ ] CURR_DATE()

### 10. Which of the following indexes would be best for fast lookup for exact key matches but not so good for prefix lookups or sorting?
- [ ] EXACT
- [x] HASH
- [ ] INDEX2
- [ ] BTREE

### 11. Why is it a good idea to add "CONSTRAINT FOREIGN KEY" statements when creating database tables? (Check all that apply)
- [x] So that you can specify default behaviors when records are deleted or updated
- [x] So that database modeling tools know the relationships between tables
- [x] So that PostgreSQL knows which columns are foreign keys and which columns are just integers
- [ ] So that prefix-based lookups perform well

### 12. When you add an index to a field in a database table, how are performance and storage affected?
- [ ] Read performance is faster, insert performance is the same, and no extra storage is required
- [ ] Read performance is the same, insert performance is faster, and no extra storage is required
- [x] Read performance is faster, insert performance is slower, and extra storage is required
- [ ] Read performance is faster, insert performance is faster, and extra storage is required


--- 
> [Database Design and Basic SQL in PostgreSQL](https://www.coursera.org/learn/database-design-postgresql/) {Week-3}
