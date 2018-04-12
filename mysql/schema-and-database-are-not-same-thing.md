# "Schema" and "Database" Are Not the Same Thing!

I thought I was a pretty good database developer. I wouldn't call myself a DBA or a "guru", but I would have put myself in the upper 50%.

The more you know, the less you know.

I was reading [this excellent blog post comparing relational databases][1], and I came across this gem:

> First things first: "schema" doesn't always mean the same thing. To MySQL, "schema" is synonymous with "database". For Postgres, a "schema" is a namespace within a database, which allows you to group tables, views, and functions together without having to break them apart into different databases.

Bottom line: You can call a database a schema in MySQL, but if you do in Postgres (or other languages?) you will be wrong.

I guess that's that.

[1]:https://dev.to/dmfay/the-ultimate-postgres-vs-mysql-blog-post-1l5
