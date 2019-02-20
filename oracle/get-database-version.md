# Get (Oracle) Database Version

I've been working with Oracle lately, and the first Oracle-specific thing I had to do was check the version.

This easy answer comes from [TechOnTheNet][1]

```sql
SELECT * FROM v$version;
```

[1]: https://www.techonthenet.com/oracle/questions/version.php