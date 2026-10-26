# Day 1: SELECT, FROM, WHERE

## 1. First 10 rows
```sql
SELECT * FROM tutorial.us_housing_units LIMIT 10;
```
Shows all columns for the first 10 rows.

## 2. Two columns
```sql
SELECT year, month FROM tutorial.us_housing_units;
```
Returns only the year and month columns.

## 3. Number above a value
```sql
SELECT * FROM tutorial.us_housing_units WHERE south > 20;
```
Filters rows where the south column is above 20.

## 4. Two conditions
```sql
SELECT * FROM tutorial.us_housing_units WHERE south > 20 AND west > 15;
```
Keeps only rows that meet both conditions.

## 5. Text pattern
```sql
SELECT * FROM tutorial.us_housing_units WHERE month_name LIKE 'J%';
```
Finds rows where the month name starts with J.
