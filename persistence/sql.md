# SQL

## CRUD Operations

```sql
INSERT INTO tasks ('title', 'status')
VALUES ('Buy groceries', 'incomplete'), ('Gas car', 'incomplete')
```

```sql
DELETE from tasks
WHERE status='complete'
```

```sql
UPDATE tasks SET status='incomplete'
WHERE title='Buy groceries'
```

## `SELECT` Basics

### `AND`		test two or more conditions.

```sql
SELECT name , continent FROM world
WHERE area < 2000
AND gdp > 5000000000
```



### `IN` 		check if item is in a list.

```sql
SELECT name, population FROM world
WHERE name IN ('Denmark', 'Finland', 'Norway', 'Sweden')
```



### `LIKE`		allows pattern matching. `%` is wildcard.

```sql
SELECT name FROM world
WHERE name LIKE 'G%'
```



### `BETWEEN`		allows range checking (always inclusive).

```sql
SELECT name, area/1000 FROM world
WHERE area BETWEEN 207600 AND 244820
```



## `SELECT` Within `SELECT` (Subqueries)

e.g. List each country where the population is larger than Russia’s:

```sql
SELECT name FROM world
WHERE population >
(SELECT population FROM world WHERE name='Russia')
```



### `ALL`		check a condition over an entire list.

```sql
SELECT name FROM world
WHERE gdp >
ALL (SELECT gdp FROM world WHERE continent = 'Europe')
```



## Using `WITH`

Provides a means to write subqueries for use in a larger `SELECT` query.

The subqueries, which are often referred to as Common Table Expressions or CTEs, can be thought of as defining temporary tables that exist just for this query.

Check out: http://www.postgresql.org/docs/9.3/static/queries-with.html

```sql
WITH regional_sales AS (
  /* subquery for total regional sales */
  SELECT region, SUM(amount) AS total_sales
  FROM orders
  GROUP BY region
),
top_regions AS (
  /* subquery for regions with most sales */
  SELECT region
  FROM regional_sales
  WHERE total_sales > (SELECT SUM(total_sales)/10 FROM regional_sales)
)
/* display sales figures per product in top regions only */
SELECT region,
       product,
       SUM(quantity) AS product_units,
       SUM(amount) AS product_sales
FROM orders
WHERE region IN (SELECT region FROM top_regions)
GROUP BY region, product;
```



## Aggregate Functions

### `SUM`		returns the sum of values!

```sql
SELECT SUM(population)
FROM world
```



### `COUNT`		returns the total number of a given value

```sql
SELECT COUNT(name) FROM world
WHERE area >= 1000000
```



### `DISTINCT`	returns only one instance of each value

```sql
SELECT DISTINCT continent FROM world
```



### `GROUP BY` 	applies `SUM` and `COUNT` to groups of values

```sql
SELECT continent, SUM(population) FROM world
GROUP BY continent
```



### `HAVING`		allows you to filter groups displayed

```sql
SELECT continent FROM world
GROUP BY continent
HAVING SUM(population)>500000000
```



### `ORDER BY`	sort results by a given value (lowest to highest)

```sql
SELECT id, title, yr
FROM movie
WHERE title LIKE '%Star Trek%'
ORDER BY yr
```



```sql
AVG()     /* Returns the average value  */
FIRST()   /* Returns the first value    */
LAST()    /* Returns the last value     */
MAX()     /* Returns the largest value  */
MIN()     /* Returns the smallest value */
```

## Joining Tables

### `JOIN`		combine databases by linking specific columns

```sql
SELECT player
FROM game JOIN goal ON id=matchid

LEFT JOIN include rows from the left table even when the linking value is null.

RIGHT JOIN  include rows from the right table even when the linking value is null.
```



## Miscellaneous

### `NULL`		null values. cannot use ‘=‘ or ‘!=‘, but rather IS and IS NOT.

```sql
SELECT name
FROM teacher
WHERE dept IS NULL
```

### `COALESCE`	takes any number of arguments and returns the first value that is not null.

```sql
SELECT name, COALESCE(mobile, home, ‘no number’)
FROM addresses
```


### `CASE`		allows you to test conditions.

```sql
SELECT name, population,
  CASE WHEN population<1000000
    THEN 'small'
    WHEN population<10000000
    THEN 'medium'
    ELSE 'large'
  END
FROM world
```

---

## CKU: SQL & BigQuery

* <https://bigquery.cloud.google.com/table/publicdata:samples.shakespeare?pli=1>

### Outline

* Syntax, concepts
* Access to CK Data
* Lab

```sql
SELECT
  state,
  is_male,
  AVG(weight_pounds) AS avg_weight,
FROM
  [publicdata:samples.natality]
WHERE
  is_male= FALSE
  AND plurality = 1
  AND state = 'CA'
  AND mother_age > father_age
GROUP BY
  state,
  is_male
```

Same as

```sql
SELECT
  state,
  is_male,
  AVG(weight_pounds) AS avg_weight,
FROM
  [publicdata:samples.natality]
WHERE
  is_male= FALSE
  AND plurality = 1
  AND state = 'CA'
  AND mother_age > father_age
GROUP BY
  1,
  2
```

---

```sql
SELECT
  year,
  is_male,
  AVG(weight_pounds) AS avg_weight,
FROM
  [publicdata:samples.natality]
WHERE
  plurality = 1
GROUP BY
  1,
  2
ORDER BY
  year,
  is_male
```

* `WHERE` only effects each row
* `HAVING` only effects each group

```sql
SELECT
  CASE WHEN weight_pounds > 8 THEN 'Heave' ELSE 'Light' END AS weight_group,
  COUNT(*) AS cnt
FROM
  [publicdata:samples.natality]
WHERE
  plurality = 1
GROUP BY
  1
```

* Filtering goes faster than joining. perhaps one day we'll just have one giant table.

```sql
SELECT
  *
FROM
  [publicdata:samples.shakespeare]
WHERE
  word_count > 100
  AND corpus_date > 1600
  AND SUBSTR(word,1,2) = 'wi'
  AND LENGTH(word) = 4
ORDER BY
  word_count DESC
```
