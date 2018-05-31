# You Can't Add An Index to a MySQL View

I hadn't realized this until today: MySQL views can't have indexes!

So I have this somewhat massive view which groups five separate tables for MLS properties. Something like:

```sql
CREATE VIEW view_listings AS 
SELECT 
	`LISTINGID`, ...
FROM (
		SELECT `LISTINGID`, ...
		FROM `residentialproperty`
	UNION
		SELECT `LISTINGID`, ...
		FROM `property`
	UNION
		SELECT `LISTINGID`, ...
		FROM `multifamily`
	UNION
		SELECT `LISTINGID`, ...
		FROM `mobilehome`
	UNION
		SELECT `LISTINGID`, ...
		FROM `lotsandland`
	UNION
		SELECT `LISTINGID`, ...
		FROM `commercial`
) `listings`
```

This works fine, more or less, except that it's pretty slow! Obviously, because it's querying five separate tables. Adding an index should greatly improve the search time for this view, right?

The "obvious fix", or so I thought, was to create an index on the listingid field.

```sql
CREATE UNIQUE INDEX get_listing_by_id ON view_listings ( listingID ) COMMENT "Index the view by id";
```

Unfortunately, here's what I got: `'mydb.view_listings' is not BASE TABLE`. I feel like this should have been mentioned in the [MySQL `CREATE INDEX` docs][1], but whatever. A little more digging turned up [this better explanation of why MySQL views simply can't support indexing and so forth][2].

Back to the drawing board on performance for that bad boy.

[1]: https://dev.mysql.com/doc/refman/8.0/en/create-index.html
[2]: https://stackoverflow.com/a/22545866