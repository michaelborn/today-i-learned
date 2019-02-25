# Formatting Dates in Oracle

Trying to retrieve records by modifiedDate, right?

```sql
SELECT * FROM records
WHERE modifiedDate = '2019-02-12'
```

This finds no results - why? Because `modifiedDate` is a timestamp column, and we need to trim the time so the user can filter by date only.

```sql
SELECT * FROM records
WHERE TO_CHAR(modifiedDate,'YYYY-MM-DD') = '2019-02-12'
```

Good old `TO_CHAR()` to the rescue!