```
  # Do not copy if you are taking the test.
```
--- 

# Graded Task: Musical Tracks Many-to-One


Create necessary tables for the assignment:
```
CREATE TABLE album (
  id SERIAL,
  title VARCHAR(128) UNIQUE,
  PRIMARY KEY(id)
);

CREATE TABLE track (
    id SERIAL,
    title VARCHAR(128),
    len INTEGER, rating INTEGER, count INTEGER,
    album_id INTEGER REFERENCES album(id) ON DELETE CASCADE,
    UNIQUE(title, album_id),
    PRIMARY KEY(id)
);

DROP TABLE IF EXISTS track_raw;
CREATE TABLE track_raw
 (title TEXT, artist TEXT, album TEXT, album_id INTEGER,
  count INTEGER, rating INTEGER, len INTEGER);
```
Load [this CSV data](https://www.pg4e.com/tools/sql/library.csv) file into the `track_raw` table using the `\copy` command. 
```
\copy track_raw(title, artist, album, count, rating, len) FROM 'library.csv' DELIMITER ',' CSV
```
Then write SQL commands to insert all of the **distinct** albums into the `album` table (creating their primary keys) 
```
INSERT INTO album (title)
  SELECT DISTINCT album FROM track_raw ORDER BY album;
```
then set the `album_id` in the `track_raw` table using an SQL query like:
```
UPDATE track_raw SET album_id = (SELECT album.id FROM album WHERE album.title = track_raw.album);
```
Then use a INSERT ... SELECT statement to copy the corresponding data from the `track_raw` table to the track table, effectively dropping the `artist` and `album` text fields.
```
INSERT INTO track (title, len, rating, count, album_id)
  SELECT title, len, rating, count, album_id
  FROM track_raw;
```

Now check if everything worked as expected: 
```
SELECT track.title, album.title
    FROM track
    JOIN album ON track.album_id = album.id
    ORDER BY track.title LIMIT 3;
```
The expected result of this query on your database is:
```
           title            |               title
----------------------------+------------------------------------
 A Boy Named Sue (live)     | The Legend Of Johnny Cash
 A Brief History of Packets | Computing Conversations
 Aguas De Marco             | Natural Wonders Music Sampler 1999

```

--- 
> [Intermediate PostgreSQL](https://www.coursera.org/learn/intermediate-postgresql/) {Week-2}

