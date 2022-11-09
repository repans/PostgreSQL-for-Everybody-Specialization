```
  # Do not copy if you are taking the test.
```
--- 

# Text In Databases

### 01. Which of the following SQL features is most affected by the addition of an index on a table?
- [ ] Text document ranking 
- [ ] String concatenation in SELECT statements 
- [x]  • WHERE clauses 
- [ ] The amount of storage taken by a TEXT column 

### 02. Why does PostgreSQL store rows in blocks with some space unused on disk?
- [ ] To allow for effective compression of plain text columns
- [ ] To give some areas of the disk drive a break to avoid overheating
- [x]  • To allow for small changes or insertions of rows to be done without rewriting the entire file
- [ ] To make best use of the time spent waiting for rotational delay

### 03. What is the typical block size used by PostgreSQL? 
- [ ] 32K 
- [ ] 1K 
- [x]  • 8K 
- [ ] 1MB 

### 04. What is a problem caused by a block size that is too small?
- [ ] Memory cache can hold fewer blocks 
- [x]  • Fragmentation 
- [ ] Disk drive temperature 
- [ ] Large blocks can be read from SSD devices more quickly 

### 05. What is the advantage of a HASH index over a B-tree index in PostgreSQL?
- [x]  • The B-tree must store the entire key value 
- [ ] The HASH index is always balanced 
- [ ] The HASH index is able to store the original key value 
- [ ] The HASH index is able to quickly find rows that match a prefix value 

### 06. What kinds of key patterns work well with a BRIN index in PostgreSQL? 
- [ ] When the key values are completely random 
- [x]  • When the rows in a block have key values in a nice tight range 
- [ ] When most lookups are done with regular expressions in WHERE clauses 
- [ ] When the key values are very long strings 

### 07. Which of the following is a PostgreSQL "inverted" index? 
- [ ] HASH 
- [x]  • GIN 
- [ ] B-tree 
- [ ] BRIN 

### 08. Which of the following describes "stop word" in natural language indexing? 
- [ ] A word used to truncate the columns on a SELECT statement 
- [ ] A word that removes a search result from a list of results 
- [x]  • A word that contributes no meaning to a query 
- [ ] A word that breaks the loop while retrieving a long list of records 

### 09. Which of the following is false about Google's search? 
- [ ] Google ranks pages based on the quality of the sites that link to them 
- [x]  • Google reads web content from sites to produce the results for each search 
- [ ] Google search uses a distributed inverted index 
- [ ] Google search uses a single very large server for each search 
- [ ] Google searches its copy of the web 

### 10. What does the PostgreSQL unnest() function do? 
- [ ] It computes a logical key from the hash value of that key 
- [x]  • It takes an array and expands it into a list of rows, one for each element in the array 
- [ ] It scans down a branch of a B-tree to find the depth of the tree 
- [ ] It reverses the multiple iterations of a two-way encryption like AES 


### 11. What Python function is most like the PostgreSQL string_to_array() function?
- [ ] trim() 
- [x]  • split() 
- [ ] String.split()  
- [ ] explode() 
- [ ] strtok() 

 
### 12. What does it mean when you add 'DISTINCT' to a SELECT statement?
- [ ] Rows that take more than 0.25 seconds to retrieve are ignored 
- [x]  • All of the returned rows are unique. 
- [ ] The query runs until a stop word is encountered 
- [ ] The rows are sorted with the "most distinctive" rows appearing first 


### 13. In PostgreSQL 11, what is the operator class used to build an index to speed up queries that use the '<@' operator?
- [ ] range_ops 
- [x]  • array_ops 
- [ ] at_ops 
- [ ] _text_ops 
- [ ] psy_ops 


### 14. Why do we reduce words to their stems when building an inverted index for natural language documents?
- [ ] To add metadata to each stored document
- [ ] To produce a language-independent search
- [ ] To make all keys the same length
- [x]  • To map multiple words with equivalent meaning to a single stem


### 15. Which of the following is an advantage of the GiST over the GIN index in PostgreSQL? 
- [x]  • Fast inserts and updates 
- [ ] Retrieves the minimum number of blocks for a query 
- [ ] Supports stop words and stemming 
- [ ] Handles mapping all lexemes to lower case 


### 16. Which came first, the tsquery or the tsvector?
- [ ] tsquery 
- [x]  • tsvector 


### 17. What function do you apply to a column to build a natural language full-text index on that column? 
- [ ] string_to_array()  
- [ ] tsquery  
- [x]  • tsvector  
- [ ] e.trim()  
- [ ] unnest  



### 18. What PostgreSQL operator checks to see if a tsquery matches a tsvector?
- [ ] IS NULL 
- [ ] LIKE 
- [x]  • @@ 
- [ ] <@ 



--- 
> [JSON and Natural Language Processing in PostgreSQL](https://www.coursera.org/learn/json-natural-language-processing-postgresql/) {[Week-2](https://www.coursera.org/learn/json-natural-language-processing-postgresql/home/week/2)}

