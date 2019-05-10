# Rename a Column in SQL Server

Trying to rename a column today in an MSSQL database. I expected the standard `ALTER TABLE x CHANGE oldColumn newColumn <type>` to work, but apparently that's a MySQL-only thing? Instead I did a quick Google search and came up with this nugget:

```sql
EXEC sp_rename
    @objname = "pages.permalink",
    @newname = "slug",
    @objtype = "COLUMN";
```

Thanks to [DustyReagan.com](http://dustyreagan.com/how-to-rename-table-or-column-using-t/), or check out the [full docs for `sp_rename` in Transact-SQL](https://docs.microsoft.com/en-us/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql?view=sql-server-2017).