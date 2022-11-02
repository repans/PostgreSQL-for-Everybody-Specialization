```
  # Do not copy if you are taking the test.
```
--- 

# Graded Task: Building an Inverted Index using SQL 
## Reverse Index in SQL 


Create needed tables for the assignment:
```
CREATE TABLE docs01 (id SERIAL, doc TEXT, PRIMARY KEY(id));

CREATE TABLE invert01 (
  keyword TEXT,
  doc_id INTEGER REFERENCES docs01(id) ON DELETE CASCADE
);
```

Insert given data into docs01: 
```
INSERT INTO docs01 (doc) VALUES
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

Now according to the requirements,  produce a reverse index from **docs01** table in lower case and store those output into **invert01** table -
```
INSERT INTO invert01 (doc_id, keyword) 
SELECT DISTINCT id, lower(s.keyword) AS keyword 
FROM docs01 AS D, unnest(string_to_array(D.doc, ' ')) s(keyword) ORDER BY id;
``` 



Now check if everything worked as expected:
```
SELECT keyword, doc_id FROM invert01 ORDER BY keyword, doc_id LIMIT 10;
```

The expected result of this query on your database is: 
```
keyword    |  doc_id
-----------+--------
a          |    1    
a          |    6    
a          |    8    
a          |    9    
about      |    1    
after      |    3    
already    |    8    
am         |    10   
and        |    1    
and        |    2   
```


--- 
> [JSON and Natural Language Processing in PostgreSQL](https://www.coursera.org/learn/json-natural-language-processing-postgresql/) {[Week-1](https://www.coursera.org/learn/json-natural-language-processing-postgresql/home/week/1)}

