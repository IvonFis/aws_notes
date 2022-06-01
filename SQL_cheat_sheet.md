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

### GROUP BY
We need to choose a categorical column to GROUP BY. 

```sql
SELECT category, division SUM(data_col)
FROM tabl
GROUP BY category, division
```
or 

```sql
SELECT category, SUM(data_col)
FROM tabl
WHERE category != 'A'
GROUP BY category
ORDER BY SUM(data_col)
```
```sql
SELECT DATE(TIMESPTAMP_DATE), SUM(amount)  FROM payment
GROUP BY DATE(TIMESTAMP_DATE)
```

### HAVING
The having clause allow us to filter **after** an aggregation has already taken place. 

```sql
SELECT company, SUM(sales)
FROM tbl
WHERE != 'Google'
GROUP BY company
HAVING SUM(sales) > 1000;
```

Having allow us to aggregate result as a filter along with a GROUP BY.

### JOIN

```sql
SELECT district, email FROM address
INNER JOIN customer ON
adress.adress_id = customer.adress_id
WHERE district = 'CALIFORNIA'
```

### GROUP BY vs HAVING
![image](https://user-images.githubusercontent.com/33365899/170773313-f2e93a66-5f2e-4556-86ed-09449c0df963.png)

### DELETE, TRUNCATE and TRUNCATE

*DELETE* With the help of the “DELETE” command, we can either delete all the rows in one go or can delete rows one by one. i.e., we can use it as per the requirement or the condition using the Where clause. It is comparatively slower than the TRUNCATE command.

*TRUNCATE* It is used to drop the whole table

*DROP* It is used to delete all the rows of a relation (table) in one go.  By using this command the existence of all the rows of the table is lost. It is comparatively faster than the delete command as it deletes all the rows fastly. 

## Aggregate functions

Their main idea is to take multiple inputs and return a single outpuT, as:

```sql
AVG() - returns a float. You could use ROUND()
COUNT()
MAX()
MIN()
SUM()
```
Happening only on SELECT and HAVING clause. 

Example

Returns the minimum and maximum price from the table catalog

```sql
SELECT MIN(cost), MAX(cost)
from catalog;
```

Retuns the average of the price with 2 decimal places from the table catalog

```sql
SELECT ROUND(AVG(price, 2))
from catalog;
```

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
## LOGICAL OPERATIONS

CASE
```sql
SELECT
SUM(
CASE rating
 WHEN 'R' THEN 1 ELSE 0
  END
) AS r
FROM film
SUM(
CASE rating
 WHEN 'PG' THEN 1 ELSE 0
  END
) AS pg
FROM film
```
COALESCE

It accepts an unlimited number of arguments. Returns the first argument that is not null.

```sql
SELECT item, (price - COALESCE(discount, 0))
AS final FROM table
```
CAST
Lets you convert one datatype into another

```sql
SELECT item, CAST(date AS TIMESTAMP) AS new_date
AS final FROM table
```

NULLIF
Takes two inputs and returns NULL If both are equal, otherwise it return the first argument passed. Ex. NULLIF(10,12)=null, NULLIF(12,10)=12

## OTHER EXPAMPLES

```sql
SELECT "date_parse"("concat"(CAST(fecha AS varchar), ' ', CAST(hora - 1 AS varchar)), '%Y-%m-%d %H') TIMESTAMP, *
FROM "eoncenace"."pmlmensual"
WHERE clavedelnodo='05CHU-230' AND fecha > DATE('2022-04-26') AND NOT (hora=25)
```

```sql
sele = 'SELECT avg(local_marginal_price_mxn_mwh) as MEAN, stddev_pop(local_marginal_price_mxn_mwh) as STD'
    fro = 'FROM "cenace_parquet"."rtm_lmp"'
    whe = 'WHERE date BETWEEN date(' + str('\'' + str(date1) + '\'') + ') AND date(' + str('\'' + str(date2) + '\'') + ');'
```

```sql
sele1 = 'SELECT nodos.clave, YEAR(pml.date) AS year, MONTH(pml.date) AS month, '
    sele2 = 'AVG(pml.local_marginal_price_mxn_mwh) AS pml, nodos.sistema, nodos.centro_de_control_regional, '
    sele3 = 'nodos.zona_de_carga, nodos.entidad_federativa_inegi'
    sele = sele1 + sele2 + sele3
    fro = 'FROM "cenace_parquet"."dam_lmp" AS pml'
    joiin = 'JOIN "cenace_nodes"."nodes" AS nodos ON pml.node_id=nodos.clave'
    gby = 'GROUP BY clave, sistema, YEAR(pml.date), MONTH(pml.date), centro_de_control_regional, zona_de_carga, entidad_federativa_inegi'
    odby = 'ORDER BY clave, year, month;'
```

```sql
calling_string_mda = '''
    WITH dhours AS (
        SELECT
            DISTINCT hour
        from
            "cenace_parquet"."dam_lmp"
    ),
    schedule AS (
        SELECT
            hour,
            CASE
                WHEN hour >= 8
                AND hour <= 18 THEN 'dia'
                ELSE 'noche'
            END AS tipo
        FROM
            dhours
    ),
    daily AS (
        SELECT
            lmp.date,
            lmp.node_id,
            schedule.tipo,
            AVG(lmp.local_marginal_price_mxn_mwh) AS average
        FROM
            "cenace_parquet"."dam_lmp" as lmp
            LEFT JOIN schedule ON schedule.hour = lmp.hour
        WHERE
            lmp.node_id IN ('05LZM-115', '03BFM-230')
            AND lmp.date >= current_date - interval '1' day
        GROUP BY
            lmp.date,
            lmp.node_id,
            schedule.tipo
    ),
    yearly AS (
        SELECT
            lmp.node_id,
            schedule.tipo,
            AVG(lmp.local_marginal_price_mxn_mwh) AS average
        FROM
            "cenace_parquet"."dam_lmp" as lmp
            LEFT JOIN schedule ON schedule.hour = lmp.hour
        WHERE
            lmp.node_id IN ('05LZM-115', '03BFM-230')
            AND year(lmp.date) = year(current_date)
        GROUP BY
            lmp.node_id,
            schedule.tipo
    )

    SELECT
        daily.node_id,
        daily.date,
        daily.tipo,
        round(daily.average, 2) AS lmp,
        round(yearly.average, 2) AS lmp_average
    FROM
        daily
        JOIN yearly ON daily.node_id = yearly.node_id AND daily.tipo = yearly.tipo
    ORDER BY node_id, date, tipo'''


calling_string_mtr = '''
    WITH dhours AS (
            SELECT
                DISTINCT hour
            from
                "cenace_parquet"."rtm_lmp"
        ),
        schedule AS (
            SELECT
                hour,
                CASE
                    WHEN hour >= 8
                    AND hour <= 18 THEN 'dia'
                    ELSE 'noche'
                END AS tipo
            FROM
                dhours
        ),
        daily AS (
            SELECT
                lmp.date,
                lmp.node_id,
                schedule.tipo,
                AVG(lmp.local_marginal_price_mxn_mwh) AS average
            FROM
                "cenace_parquet"."rtm_lmp" as lmp
                LEFT JOIN schedule ON schedule.hour = lmp.hour
            WHERE
                lmp.node_id IN ('05LZM-115', '03BFM-230')
                AND lmp.date = current_date - interval '4' day
            GROUP BY
                lmp.date,
                lmp.node_id,
                schedule.tipo
        ),
        yearly AS (
            SELECT
                lmp.node_id,
                schedule.tipo,
                AVG(lmp.local_marginal_price_mxn_mwh) AS average
            FROM
                "cenace_parquet"."rtm_lmp" as lmp
                LEFT JOIN schedule ON schedule.hour = lmp.hour
            WHERE
                lmp.node_id IN ('05LZM-115', '03BFM-230')
                AND year(lmp.date) = year(current_date)
            GROUP BY
                lmp.node_id,
                schedule.tipo
        )

        SELECT
            daily.node_id,
            daily.date,
            daily.tipo,
            round(daily.average, 2) AS lmp,
            round(yearly.average, 2) AS lmp_average
        FROM
            daily
            JOIN yearly ON daily.node_id = yearly.node_id AND daily.tipo = yearly.tipo
        ORDER BY node_id, date, tipo'''
```
