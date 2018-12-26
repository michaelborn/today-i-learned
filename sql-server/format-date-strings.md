# How To Format Date Strings in SQL Server

Where `chr(10)` is the myDateField column type to expect and `103` is the date format to use. The 100-plus date format codes will display a 4-digit year, whereas the 0-100 codes will display a 2-digit year. (Not recommended, if you ask me!)

So, to generate a standard `mm/dd/yyyy` date format: 

```sql
CONVERT( chr(10), myDateField, 103)
```

See the [SQL Server CAST and CONVERT docs][2] for a full reference of the various date formats you can use.

For more info, you can [read this post from sql-server-helper.com which gives more detail and more concrete examples][3].

[1]: https://stackoverflow.com/questions/889629/how-to-get-a-date-in-yyyy-mm-dd-format-from-a-tsql-datetime-field
[2]: https://docs.microsoft.com/en-us/sql/t-sql/functions/cast-and-convert-transact-sql?view=sql-server-2017
[3]: http://www.sql-server-helper.com/tips/date-formats.aspx
