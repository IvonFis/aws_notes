# SQL commands
---

## SQL SELECT STATEMENTS

SELECT all the rows and columns FROM table tbl

```sql
 SELECT * FROM tbl
```

SELECT columns c1, c2 with WHERE condition. and ORDER BY c1 in ascending order ASC ans c2 in descending DESC

```sql
SELECT c1, c2 FROM tbl
WHERE conditions
ORDER BY c1 ASC, c2 DESC
```
Example

```sql
SELECT * FROM payment
WHERE amount != 0.00
ORDER BY payment_date DESC
LIMIT 5;
```

SELECT DISTINCT rows columns c1 and c2 FROM table tbl

```sql
SELECT DISTINCT c1, c2
FROM tbl
```

SELECT how many (COUNT function) unique DISTINCT values from column 1 FROM table

```sql
SELECT COUNT(DISTINCT(c1))
FROM tbl
```

SELECT column c1 and use AGGREGATE function on expression expr, GROUP BY columns c1.

```sql
SELECT c1, AGGREGATE(exp)
FROM tbl
GROUP BY c1
```

SELECT columns c1 and c2 as column alias of the result AGRREGATE function on exp. filter group of records with c2 HAVING a value greater than v

```sql
SELECT c1, AGGREGATE(exp) AS c2
FROM tbl
GROUP BY c1
HAVING C2 > v
```

SELECT value BETWEEN (NOT BETWEEN) limits
> For format dates ISO 8601 standard format, YYYY-MM-DD

```sql
SELECT * FROM tabl
WHERE amout BETWEEN 8 AND 10 
AND BETWEEN '2007-03-02' AND '2007-04-22';
```

SELECT multiple values IN (NOT IN) column

```sql
SELECT * FROM tabl
WHERE amount IN (0.99, 1, 32) AND node NOT IN ('QUERETARO', 'HERMOSILLO');
```

SELECT values with a pattern matching string against data LIKE characters
> Use % for match any sequence of characters (begin with A = %A, end with a = %a)
> Use _ for match any single character

```sql
SELECT * FROM tabl
WHERE name LIKE '_her%'

> *C*heryl
> *t*heresa
```

### GROUP BY vs HAVING
![image](https://user-images.githubusercontent.com/33365899/170773313-f2e93a66-5f2e-4556-86ed-09449c0df963.png)

### DELETE, TRUNCATE and TRUNCATE

*DELETE* With the help of the “DELETE” command, we can either delete all the rows in one go or can delete rows one by one. i.e., we can use it as per the requirement or the condition using the Where clause. It is comparatively slower than the TRUNCATE command.

*TRUNCATE* It is used to drop the whole table

*DROP* It is used to delete all the rows of a relation (table) in one go.  By using this command the existence of all the rows of the table is lost. It is comparatively faster than the delete command as it deletes all the rows fastly. 

## SQL UPDATE TABLE

UPDATE data into table tbl

```sql
 INSERT INTO tbl(c1,c2,c4)
 VALUES(d1,d2,d4)
```

INSERT data from table2 to table 1

```sql
 INSERT INTO tbl(c1,c2)
 SELECT c1, c2 FROM tbl2
 WHERE conditions
```

UPDATE data in table

```sql
 UPDATE t
 SET c1=v1, c2=v2
 WHERE conditions
```

DELETE records based on there conditons

```sql
DELETE from tbl
WHERE conditions
```

DROP table tnl and re-create it, all data is lost

```sql
 TRUNCATE TABLE tbl
```

## SQL TABLE STATEMENTS

Create table with primary keys is c1

```sql
 TRUNCATE TABLE tbl
  c1 datatype(length)
  c2 datatype(length)
  ...
  PRIMARY KEY(c1)
```

DROP table, remove the table from the database

```sql
DROP TABLE tbl
```

ALTER table, add column c1 to table tbl

```sql
ALTER TABLE tbl
ADD COLUMN c1 datatype(c1)
```

ALTER table, DROP column c1 from table b1

```sql
ALTER TABLE tbl
DROP column c1
```

## SQL JOIN STATEMENTS

JOIN inner table tbl1 and tbl2 based on joined conditions

```sql
SELECT * FROM tbl1
INNER JOIN tbl2 ON join conditions
```

JOIN LEFT/RIGHT TABLE tbl1 with tbl2 based on join conditions

```sql
SELECT * FROM tbl1
LEFT JOIN tb2 ON join conditions

or

RIGHT JOIN tb2 ON join conditions
```


