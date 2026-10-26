# Day 2: ORDER BY, DISTINCT and Aggregates

## Concepts
- `ORDER BY` sorts results (`DESC` = highest first)
- `DISTINCT` removes duplicate values
- Aggregates (`COUNT`, `SUM`, `AVG`, `MIN`, `MAX`) summarize many rows into one value
- `AS` gives a result a readable name

## 1. Top 5 rows by west
```sql
SELECT * FROM tutorial.us_housing_units
ORDER BY west DESC
LIMIT 5;
```
Sorts by west from highest to lowest and shows the top 5 rows.

## 2. Distinct years
```sql
SELECT DISTINCT year FROM tutorial.us_housing_units;
```
Lists each year once, with no duplicates.

## 3. Count rows
```sql
SELECT COUNT(*) FROM tutorial.us_housing_units;
```
Counts the total number of rows in the table.

## 4. Average of south
```sql
SELECT AVG(south) AS avg_south
FROM tutorial.us_housing_units;
```
Calculates the average of the south column and names it avg_south.

## 5. Highest and lowest midwest
```sql
SELECT MAX(midwest) AS highest_midwest,
       MIN(midwest) AS lowest_midwest
FROM tutorial.us_housing_units;
```
Returns the highest and lowest midwest values in one query.

## 6. Bonus: average south since 2005
```sql
SELECT AVG(south) AS avg_south_2005_plus
FROM tutorial.us_housing_units
WHERE year >= 2005;
```
Averages south only for rows from 2005 onward.

## What I learned
- `DISTINCT` shows unique values; `COUNT(*)` counts rows.
- `WHERE` filters rows before the aggregate is calculated.
