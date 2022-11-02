```
  # Do not copy if you are taking the test.
```
--- 

# Graded Task: Unesco Heritage Sites Many-to-One


Create tables that will needed for the assignment:
```
DROP TABLE unesco_raw;
CREATE TABLE unesco_raw (
    name TEXT, 
    description TEXT, 
    justification TEXT, 
    year INTEGER,
    longitude FLOAT, 
    latitude FLOAT, 
    area_hectares FLOAT,
    category TEXT, 
    category_id INTEGER, 
    state TEXT, 
    state_id INTEGER,
    region TEXT, 
    region_id INTEGER, 
    iso TEXT, 
    iso_id INTEGER
);

CREATE TABLE category (
  id SERIAL,
  name VARCHAR(128) UNIQUE,
  PRIMARY KEY(id)
);
```

To load [the CSV data for this assignment](https://www.pg4e.com/tools/sql/whc-sites-2018-small.csv) use the following copy command. 
Adding **HEADER** causes the CSV loader to skip the first line in the CSV file. 
The `\copy` command must be one long line. 
```
\copy unesco_raw(name,description,justification,year,longitude,latitude,area_hectares,category,state,region,iso) 
      FROM 'whc-sites-2018-small.csv' WITH DELIMITER ',' CSV HEADER;
```

In order to normalize the data, we need to create more tables - 

```
CREATE TABLE state (
  id SERIAL,
  name VARCHAR(128) UNIQUE,
  PRIMARY KEY(id)
);

CREATE TABLE region (
  id SERIAL,
  name VARCHAR(128) UNIQUE,
  PRIMARY KEY(id)
);

CREATE TABLE iso (
  id SERIAL,
  name VARCHAR(128) UNIQUE,
  PRIMARY KEY(id)
);
```
Now we have the necessary tables. It's time to normalize the data in the `unesco_raw` table by adding the entries to each of the lookup tables :   
 
```
INSERT INTO category (name)
  SELECT DISTINCT category FROM unesco_raw ORDER BY category;

INSERT INTO state (name)
  SELECT DISTINCT state FROM unesco_raw ORDER BY state;

INSERT INTO region (name)
  SELECT DISTINCT region FROM unesco_raw ORDER BY region;

INSERT INTO iso (name)
  SELECT DISTINCT iso FROM unesco_raw ORDER BY iso;
```

then add the foreign key columns to the `unesco_raw` table : 

```
UPDATE unesco_raw SET category_id = (SELECT category.id FROM category WHERE category.name = unesco_raw.category); 

UPDATE unesco_raw SET state_id = (SELECT state.id FROM state WHERE state.name = unesco_raw.state);

UPDATE unesco_raw SET region_id = (SELECT region.id FROM region WHERE region.name = unesco_raw.region);

UPDATE unesco_raw SET iso_id = (SELECT iso.id FROM iso WHERE iso.name = unesco_raw.iso);
``` 

At this point we need to make a new table called `unesco` that removes all of the un-normalized redundant text columns like category.
```
DROP TABLE unesco;
CREATE TABLE unesco (
    name TEXT, 
    description TEXT, 
    justification TEXT, 
    year INTEGER,
    longitude FLOAT, 
    latitude FLOAT, 
    area_hectares FLOAT,
    category_id INTEGER, 
    state_id INTEGER,
    region_id INTEGER, 
    iso_id INTEGER
);
```
Now we can populate normalized fields from `unesco_raw` to `unesco`.
```
INSERT INTO unesco (
    name, 
    description, 
    justification, 
    year,
    longitude, 
    latitude, 
    area_hectares,
    category_id, 
    state_id,
    region_id, 
    iso_id)
  SELECT 
    name, 
    description, 
    justification, 
    year,
    longitude, 
    latitude, 
    area_hectares,
    category_id, 
    state_id,
    region_id, 
    iso_id
  FROM unesco_raw;
```

Now check if everything worked as expected:
```
SELECT unesco.name, year, category.name, state.name, region.name, iso.name
  FROM unesco
  JOIN category ON unesco.category_id = category.id
  JOIN iso ON unesco.iso_id = iso.id
  JOIN state ON unesco.state_id = state.id
  JOIN region ON unesco.region_id = region.id
  ORDER BY state.name, unesco.name
  LIMIT 3;
```
The expected result of this query on your database is:
```
                    name                     | year |   name   |    name     |           name           | name
---------------------------------------------+------+----------+-------------+--------------------------+------
 Cultural Landscape and Archaeological ...   | 2003 | Cultural | Afghanistan | Asia and the Pacific     | af
 Minaret and Archaeological Remains of Jam   | 2002 | Cultural | Afghanistan | Asia and the Pacific     | af
 Butrint                                     | 1992 | Cultural | Albania     | Europe and North America | al
```


--- 
> [Intermediate PostgreSQL](https://www.coursera.org/learn/intermediate-postgresql/) {Week-2}

