# Day 3: GROUP BY and HAVING

## Concepts
- `GROUP BY` creates one result row per group
- `WHERE` filters rows before grouping; `HAVING` filters groups after
- Non-aggregate columns in `SELECT` must be in `GROUP BY`

## 1. Average south per year
```sql
SELECT year, AVG(south) AS avg_south
FROM tutorial.us_housing_units
GROUP BY year
ORDER BY year;
```
Calculates the average south value for each year.

## 2. Rows per year
```sql
SELECT year, COUNT(*) AS row_count
FROM tutorial.us_housing_units
GROUP BY year;
```
Counts how many rows exist for each year.

## 3. Total west per year, highest first
```sql
SELECT year, SUM(west) AS total_west
FROM tutorial.us_housing_units
GROUP BY year
ORDER BY total_west DESC;
```
Sums west per year and ranks years from highest to lowest.

## 4. HAVING: years with high average
```sql
SELECT year, AVG(south) AS avg_south
FROM tutorial.us_housing_units
GROUP BY year
HAVING AVG(south) > 30;
```
Shows only years where the average south value is above 30.

## 5. WHERE + GROUP BY
```sql
SELECT year, MAX(midwest) AS max_midwest
FROM tutorial.us_housing_units
WHERE year >= 2000
GROUP BY year;
```
Filters to 2000 onward first, then finds the highest midwest per year.

## What I learned
- `WHERE` filters rows; `HAVING` filters grouped results.
- Aggregates need `GROUP BY` when mixed with normal columns.
