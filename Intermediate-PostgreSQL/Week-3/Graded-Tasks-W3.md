```
  # Do not copy if you are taking the test.
```
--- 

# Graded Tasks

## Puzzle: Break a Hashing Function 

**Note:** _Try to understad the assignment. The answer is ultimately very simple. All you need to do is completely understand two lines of Python code.._ 

**Tip:** For this problem, you can choose two strings by swapping characters with three position intervals. For example `ABCFAK` and `FAKABC` will cause a collision.


## Generating Text 

In this assignment you will create a table named **bigtext** with a single TEXT column named **content**. Insert 100000 records with numbers starting at 100000 and going through 199999 into the table as shown below:

```
This is record number 100000 of quite a few text records.
This is record number 100001 of quite a few text records.
...
This is record number 199998 of quite a few text records.
This is record number 199999 of quite a few text records.
```

At first, create `bigtext` table with a single TEXT column named `content`:
```
DROP TABLE bigtext;
CREATE TABLE bigtext (
   content TEXT
);
```

Now we have to insert 100000 records with numbers starting at 100000 and going through 199999 into the table. In order to accomplish this, we can use `generate_series()` function. 

```
INSERT INTO bigtext (content) 
SELECT 'This is record number ' || generate_series(100000, 199999) || ' of quite a few text records.';
``` 

Now check if data is inserted into the table: 
```
SELECT content FROM bigtext ORDER BY content DESC LIMIT 5;
```
It should return as follows: 
```
                          content
-----------------------------------------------------------
 This is record number 199999 of quite a few text records.
 This is record number 199998 of quite a few text records.
 This is record number 199997 of quite a few text records.
 This is record number 199996 of quite a few text records.
 This is record number 199995 of quite a few text records.
 ```
 
 
        

--- 
> [Intermediate PostgreSQL](https://www.coursera.org/learn/intermediate-postgresql/) {Week-3}

