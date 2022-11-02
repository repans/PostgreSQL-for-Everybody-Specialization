```
  # Do not copy if you are taking the test.
```
--- 

# Intermediate SQL


### 1. What is the SQL command to add a column to a table?
- [ ] COLUMN-ADD
- [ ] RECREATE TABLE
- [x] ALTER TABLE
- [ ] UPDATE
- [ ] EXTEND-COLUMN

### 2. What is the SQL command to drop a column from a table?
- [ ] UPDATE
- [ ] DELETE-COLUMN
- [x] ALTER TABLE
- [ ] RECREATE TABLE
- [ ] COLUMN-DEL

### 3. What is the SQL command to change the length of a text column in a table?
- [ ] RECREATE TABLE
- [ ] UPDATE
- [x] ALTER TABLE
- [ ] COLUMN-EXTEND
- [ ] TEXT-EXTEND

### 4. What is the psql command to read commands from a file?
- [ ] sysin
- [ ] read-file
- [ ] wget
- [ ] curl
- [x] \i

### 5. How do you indicate that a column like created_at is supposed to be auto-populated when a row is inserted?
- [ ] NULL FIXED
- [ ] ONCHANGE UPDATE
- [x] DEFAULT NOW()
- [ ] AUTODATE

### 6. What is the best time zone to store things like when a record was added or updated?
- [ ] Local time zone for the server
- [ ] Local time zone for the user
- [ ] Eastern US (Standard) Time
- [x] UTC

### 7. What is the SQL function that represents the current time?
- [ ] TMZ()
- [x] NOW()
- [ ] DATE_TIME()
- [ ] CURRENT_TIME()

### 8. What does the SQL keyword DISTINCT accomplish?
- [x] It insures that there are no duplicate copies of any row in a result set
- [ ] It insures that there are spaces on either side of a word in a LIKE clause
- [ ] It makes sure that multiple clauses in a WHERE clause must all be true or all false
- [ ] It means one and only one of the of the WHERE clauses is true

### 9. What SQL technique is often used when counting the number of times a value appears in a column?
- [ ] DISTINCT
- [x] COUNT / GROUP BY
- [ ] LIMIT COUNT
- [ ] LIKE
- [ ] ORDER WHILE

### 10. What is the SQL command to start a transaction?
- [ ] COMMIT
- [ ] ROLLBACK
- [ ] START
- [x] BEGIN
- [ ] SELECT ... FOR UPDATE

### 11. What output will the following SQL sequence produce? 

Assume that the tables have been created and all the columns exist.
```
INSERT INTO Account (acct,bal) VALUES ('12345', 100);
UPDATE Account SET bal=bal+100;
BEGIN;
UPDATE Account SET bal=bal+100.
ROLLBACK;
SELECT bal FROM Account WHERE acct='12345';
```
- [ ] 300
- [x] 200
- [ ] 100
- [ ] You will get an error because ROLLBACK deletes the row that was updated
- [ ] 0

### 12. What does the "FOR UPDATE" do on a SELECT statement when a transaction has been started?
- [ ] It unlocks the row if the row was in use in annother trancsation running a the same time
- [x] It locks the row so that no other thread can SELECT or UPDATE the row until the transcaction has been completed
- [ ] It indicates that if the row is locked, we do not want to wait for it to be unlocked
- [ ] It keeps the row in memory so that a following UPDATE can be done more efficiently

### 13. In SQL, what does the RETURNING keyword accomplish?
- [ ] When a record is inserted or updated, you see the old values before the change
- [ ] It registers an event that will trigger after reach stored procedure
- [ ] It provides a return value for a stored procedure
- [x] When a record is inserted or updated, you see the resulting values

### 14. What is needed for an INSERT ... ON CONFLICT ... UPDATE to work?
- [ ] A CONFLICT constraint on a foreign key column
- [x] A UNIQUE clause on the column in question
- [ ] Either NULL or ON DELETE CASCADE on the column in the CREATE statement
- [ ] One or more SERIAL columns in the table

### 15. In general, sub-queries perform better than JOINs. 
- [ ] True
- [x] False



--- 
> [Intermediate PostgreSQL](https://www.coursera.org/learn/intermediate-postgresql/) {Week-1}

