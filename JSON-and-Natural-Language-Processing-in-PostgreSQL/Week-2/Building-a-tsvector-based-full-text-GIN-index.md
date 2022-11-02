```
  # Do not copy if you are taking the test.
```
--- 

# Building a tsvector-based full text GIN index 
## GIN ts_vector Index 

The **goal** of this assignment is to run these queries:
```
SELECT id, doc FROM docs03 WHERE to_tsquery('english', 'following') @@ to_tsvector('english', doc);
EXPLAIN SELECT id, doc FROM docs03 WHERE to_tsquery('english', 'following') @@ to_tsvector('english', doc);
```
and   
(a) get the correct document(s) and  
(b) use the GIN index (i.e. not use a sequential scan). 

---

So let's create needed table/s for the assignment:
```
CREATE TABLE docs03 (id SERIAL, doc TEXT, PRIMARY KEY(id));
```
If you already have the `docs03` filled with the correct rows (from previous assignment), you can jump to creating the new index to the table without inserting following data.

If you didn't have the `docs03` earlier, then insert following one-line documents into `docs03` table: 
```
INSERT INTO docs03 (doc) VALUES
('For example look at the following text about a clown and a car Look at'),
('the text and figure out the most common word and how many times it'),
('the clown ran after the car and the car ran into the tent'),
('and the tent fell down on the clown and the car'),
('Then imagine that you are doing this task looking at millions of lines'),
('of text Frankly it would be quicker for you to learn Python and write a'),
('Python program to count the words than it would be to manually scan the'),
('The even better news is that I already came up with a simple program to'),
('find the most common word in a text file I wrote it tested it and now'),
('I am giving it to you to use so you can save some time');
```

You should also insert a number of filler rows into the table to make sure PostgreSQL uses its index:
```
INSERT INTO docs03 (doc) SELECT 'Neon ' || generate_series(10000,20000);
``` 

Finally **create the new index**:
```
CREATE INDEX fulltext03 ON docs03 USING gin(to_tsvector('english', doc));
```

It might take from a few seconds to a minute or two before PostgreSQL catches up with its indexing. 
The autograder won't work if the index is incomplete. If the **EXPLAIN** command says that it is using **Seq Scan** - the index has not completed yet. 
Run the above **EXPLAIN** multiple times if necessary until you verify that PostgreSQL has finished making the index:

```
pg4e=> EXPLAIN SELECT id, doc FROM docs03 WHERE to_tsquery('english', 'instructions') @@ to_tsvector('english', doc);
                                  QUERY PLAN
-------------------------------------------------------------------------------
 Seq Scan on docs03  (cost=0.00..2682.89 rows=50 width=15)
   Filter: ('''instruct'''::tsquery @@ to_tsvector('english'::regconfig, doc))
(2 rows)


TIME PASSES......


pg4e=> EXPLAIN SELECT id, doc FROM docs03 WHERE to_tsquery('english', 'instructions') @@ to_tsvector('english', doc);
                                       QUERY PLAN
-----------------------------------------------------------------------------------------
 Bitmap Heap Scan on docs03  (cost=208.27..268.71 rows=35 width=36)
   Recheck Cond: ('''instruct'''::tsquery @@ to_tsvector('english'::regconfig, doc))
   ->  Bitmap Index Scan on fulltext03  (cost=0.00..208.26 rows=35 width=0)
         Index Cond: ('''instruct'''::tsquery @@ to_tsvector('english'::regconfig, doc))
(4 rows)

pg4e=>
```

---

After waiting a bit, run following commands:
```
SELECT id, doc FROM docs03 WHERE to_tsquery('english', 'following') @@ to_tsvector('english', doc);
EXPLAIN SELECT id, doc FROM docs03 WHERE to_tsquery('english', 'following') @@ to_tsvector('english', doc);
```

The expected result of those query on your database should look like:- 
```
pg4e_***=> SELECT id, doc FROM docs03 WHERE to_tsquery('english', 'following') @@ to_tsvector('english', doc);
 id |                                  doc
----+------------------------------------------------------------------------
  1 | For example look at the following text about a clown and a car Look at
(1 row)


pg4e_***=> EXPLAIN SELECT id, doc FROM docs03 WHERE to_tsquery('english', 'following') @@ to_tsvector('english', doc);
                                      QUERY PLAN
---------------------------------------------------------------------------------------
 Bitmap Heap Scan on docs03  (cost=12.39..81.75 rows=50 width=15)
   Recheck Cond: ('''follow'''::tsquery @@ to_tsvector('english'::regconfig, doc))
   ->  Bitmap Index Scan on fulltext03  (cost=0.00..12.38 rows=50 width=0)
         Index Cond: ('''follow'''::tsquery @@ to_tsvector('english'::regconfig, doc))
(4 rows)
```
Make sure that it's not a `Seq Scan`, but a `Bitmap Heap Scan`. 

**It's DONE.**

--- 
> [JSON and Natural Language Processing in PostgreSQL](https://www.coursera.org/learn/json-natural-language-processing-postgresql/) {[Week-2](https://www.coursera.org/learn/json-natural-language-processing-postgresql/home/week/2)}
