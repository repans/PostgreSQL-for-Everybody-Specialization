```
  # Do not copy if you are taking the test.
```
--- 

# Graded Task: Musical Track Database plus Artists


Create needed tables for the assignment:
```
DROP TABLE album CASCADE;
CREATE TABLE album (
    id SERIAL,
    title VARCHAR(128) UNIQUE,
    PRIMARY KEY(id)
);

DROP TABLE track CASCADE;
CREATE TABLE track (
    id SERIAL,
    title TEXT, 
    artist TEXT, 
    album TEXT, 
    album_id INTEGER REFERENCES album(id) ON DELETE CASCADE,
    count INTEGER, 
    rating INTEGER, 
    len INTEGER,
    PRIMARY KEY(id)
);

DROP TABLE artist CASCADE;
CREATE TABLE artist (
    id SERIAL,
    name VARCHAR(128) UNIQUE,
    PRIMARY KEY(id)
);

DROP TABLE tracktoartist CASCADE;
CREATE TABLE tracktoartist (
    id SERIAL,
    track VARCHAR(128),
    track_id INTEGER REFERENCES track(id) ON DELETE CASCADE,
    artist VARCHAR(128),
    artist_id INTEGER REFERENCES artist(id) ON DELETE CASCADE,
    PRIMARY KEY(id)
);
```

Load data from the [csv](https://www.pg4e.com/tools/sql/library.csv) file (same as in prior exercises). 
```
\copy track(title,artist,album,count,rating,len) FROM 'library.csv' WITH DELIMITER ',' CSV;
```

Now start normalization -
```
INSERT INTO album (title) SELECT DISTINCT album FROM track;
UPDATE track SET album_id = (SELECT album.id FROM album WHERE album.title = track.album); 

INSERT INTO tracktoartist (track, artist) SELECT DISTINCT title, artist FROM track;

INSERT INTO artist (name) SELECT DISTINCT artist FROM tracktoartist;

UPDATE tracktoartist SET track_id = (SELECT track.id FROM track WHERE tracktoartist.track = track.title);
UPDATE tracktoartist SET artist_id = (SELECT artist.id FROM artist WHERE artist.name = tracktoartist.artist); 
``` 

We are now done with these text fields 
```
ALTER TABLE track DROP COLUMN album;
ALTER TABLE track DROP COLUMN artist;
ALTER TABLE tracktoartist DROP COLUMN track;
ALTER TABLE tracktoartist DROP COLUMN artist;
```

Now check if everything worked as expected:
```
SELECT track.title, album.title, artist.name
FROM track
JOIN album ON track.album_id = album.id
JOIN tracktoartist ON track.id = tracktoartist.track_id
JOIN artist ON tracktoartist.artist_id = artist.id
LIMIT 3;
```

The expected result of this query on your database is: 
```
                title                 |     title     |     name
--------------------------------------+---------------+---------------
 Heavy                                | Brent's Album | Brent
 Jack the Stripper/Fairies Wear Boots | Paranoid      | Black Sabbath
 Asche Zu Asche                       | Herzeleid     | Rammstein
```

OR 

with ORDER BY:
```
SELECT track.title, album.title, artist.name
FROM track
JOIN album ON track.album_id = album.id
JOIN tracktoartist ON track.id = tracktoartist.track_id
JOIN artist ON tracktoartist.artist_id = artist.id
ORDER BY track.title
LIMIT 3;
```

The expected result of this query on your database is: 
```
           title            |               title                |         name
----------------------------+------------------------------------+-----------------------
 A Boy Named Sue (live)     | The Legend Of Johnny Cash          | Johnny Cash
 A Brief History of Packets | Computing Conversations            | IEEE Computer Society
 Aguas De Marco             | Natural Wonders Music Sampler 1999 | Rosa Passos
```



--- 
> [Intermediate PostgreSQL](https://www.coursera.org/learn/intermediate-postgresql/) {Week-2}

