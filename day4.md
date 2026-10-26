# Day 4: JOINs

## Concepts
- `JOIN` combines tables using a matching column
- `INNER JOIN` keeps only matches; `LEFT JOIN` keeps all rows from the left table
- Aliases (`c`, `i`) shorten table names
- `LEFT JOIN` + `WHERE ... IS NULL` finds rows with no match

## 1. Inner join: companies and their investors
```sql
SELECT c.name, c.category_code, i.investor_name
FROM tutorial.crunchbase_companies c
JOIN tutorial.crunchbase_investments_part1 i
  ON c.permalink = i.company_permalink
LIMIT 20;
```
Links each company to the investors who funded it.

## 2. Left join: companies with no investments
```sql
SELECT c.name
FROM tutorial.crunchbase_companies c
LEFT JOIN tutorial.crunchbase_investments_part1 i
  ON c.permalink = i.company_permalink
WHERE i.company_permalink IS NULL
LIMIT 20;
```
Finds companies that have no matching investment rows.

## 3. Investments per company
```sql
SELECT c.name, COUNT(*) AS investment_count
FROM tutorial.crunchbase_companies c
JOIN tutorial.crunchbase_investments_part1 i
  ON c.permalink = i.company_permalink
GROUP BY c.name
ORDER BY investment_count DESC
LIMIT 10;
```
Counts investments for each company and shows the top 10.

## 4. Total raised by category
```sql
SELECT c.category_code, SUM(i.raised_amount_usd) AS total_raised
FROM tutorial.crunchbase_companies c
JOIN tutorial.crunchbase_investments_part1 i
  ON c.permalink = i.company_permalink
GROUP BY c.category_code
ORDER BY total_raised DESC
LIMIT 10;
```
Adds up funding by industry category and ranks the top 10.

## 5. Join with a filter
```sql
SELECT c.name, i.investor_name, i.raised_amount_usd
FROM tutorial.crunchbase_companies c
JOIN tutorial.crunchbase_investments_part1 i
  ON c.permalink = i.company_permalink
WHERE c.country_code = 'USA'
ORDER BY i.raised_amount_usd DESC
LIMIT 10;
```
Shows the 10 largest investments in US-based companies.

## What I learned
- `INNER JOIN` drops unmatched rows; `LEFT JOIN` keeps them.
- Joins combine well with `GROUP BY` for business questions.
