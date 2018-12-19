# How to Show Column Types like MySQL's "Show Columns" statement

For all those MySQL devs who miss the simplicity of `SHOW CREATE TABLE myTable` or `SHOW COLUMNS FROM myTable`, here's the snippet you are looking for.

```sql
SELECT COLUMN_NAME,DATA_TYPE,CHARACTER_MAXIMUM_LENGTH,COLUMN_DEFAULT
FROM INFORMATION_SCHEMA.COLUMNS
WHERE TABLE_NAME = 'myTable'
ORDER BY COLUMN_NAME;
```

(After I wrote all that...) nevermind, use [`sp_columns` command][2], it is a lot more useful and easier to remember.

```sql
EXEC sp_columns myTable
```

[1]: https://stackoverflow.com/a/13405667/1525594
[2]: https://docs.microsoft.com/en-us/sql/relational-databases/system-stored-procedures/sp-columns-transact-sql?view=sql-server-2017
[3]: https://techcrunch.com/2013/01/19/your-database-is-probably-terrible/