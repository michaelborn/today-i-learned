# Alter Existing Constraint in Transact-SQL

First, see this quote from [Modify Unique Constraints][1]:

> To modify a UNIQUE constraint using Transact-SQL, you must first delete the existing UNIQUE constraint and then re-create it with the new definition.

This constraint (totally pun intended) extends to all sorts of constraints *and* all sorts of relational databases, by the way - NOT just unique constraints as the quote suggests, and not just SQL Server. You [just can't][5] [modify existing constraints in place][2].

So, you can [drop the constraint][3] using this:

```sql
ALTER TABLE myTable
DROP CONSTRAINT myConstraint;
```

Once the constraint has been dropped, [add the unique constraint][4] with the additional column or whatever you wanted to do:

```sql
ALTER TABLE myTable
ADD CONSTRAINT myConstraint UNIQUE (column1, column2);
```

[1]: https://docs.microsoft.com/en-us/sql/relational-databases/tables/modify-unique-constraints?view=sql-server-2017
[2]: https://stackoverflow.com/a/861173/1525594
[3]: https://docs.microsoft.com/en-us/sql/relational-databases/tables/delete-unique-constraints?view=sql-server-2017
[4]: https://docs.microsoft.com/en-us/sql/relational-databases/tables/create-unique-constraints?view=sql-server-2017
[5]: https://stackoverflow.com/a/13245101/1525594