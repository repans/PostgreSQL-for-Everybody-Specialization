```
  # Do not copy if you are taking the test.
```
--- 

# Graded Tasks

### Alter Table 
```
ALTER TABLE pg4e_debug ADD COLUMN neon757 INTEGER;
```


### SELECT DISTINCT 
```
SELECT DISTINCT state FROM taxdata ORDER BY state ASC LIMIT 5;
```


### Creating a Stored Procedure
Create `keyvalue` table first - 
```
CREATE TABLE keyvalue ( 
  id SERIAL,
  key VARCHAR(128) UNIQUE,
  value VARCHAR(128) UNIQUE,
  created_at TIMESTAMPTZ NOT NULL DEFAULT NOW(),
  updated_at TIMESTAMPTZ NOT NULL DEFAULT NOW(),
  PRIMARY KEY(id)
);
```
then run following queries - 
```
CREATE OR REPLACE FUNCTION trigger_set_timestamp()
RETURNS TRIGGER AS $$
BEGIN
  NEW.updated_at = NOW();
  RETURN NEW;
END;
$$ LANGUAGE plpgsql;
``` 
```
CREATE TRIGGER set_timestamp
BEFORE UPDATE ON keyvalue 
FOR EACH ROW
EXECUTE PROCEDURE trigger_set_timestamp();
```

--- 
> [Intermediate PostgreSQL](https://www.coursera.org/learn/intermediate-postgresql/) {Week-1}

