# Trim the TAB Character From A Field

So, I ran into a "funny" sorting issue this week. Turns out there was a `<TAB>` in a product title, causing that title to be sorted first. (Quite logic if you look at the ASCII table.)

I ran this query to trim the tab characters from the field...

```sql
UPDATE products
SET title = TRIM( title );
```

... but it turns out the function only handles spaces by default.

Here's the magic combo I settled on. (Ok, ok, [SO told me][1].)

```sql
UPDATE products
SET title = TRIM( CHAR(9) FROM title );
```

While I was at it, I checked out the [MySQL docs for the Trim() function][2], and it's actually pretty powerful. Take a gander at this:

```sql
UPDATE products
SET title = TRIM( LEADING CHAR(9) FROM title );
UPDATE pages
SET url = TRIM( TRAILING '/' FROM url );
UPDATE dummy
SET myString = TRIM( BOTH 'x' FROM myString );
```

This one's a handy one to keep in mind...

[1]: https://stackoverflow.com/a/13979261/1525594
[2]: https://dev.mysql.com/doc/refman/5.7/en/string-functions.html#function_trim