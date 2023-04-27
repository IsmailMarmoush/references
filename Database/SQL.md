## SQL

### Articles

* [visual joins](http://www.codinghorror.com/blog/2007/10/a-visual-explanation-of-sql-joins.html)
* https://javarevisited.blogspot.com/2012/12/what-is-referential-integrity-in-database-sql-mysql-example-tutorial.html#targetText=Referential%20Integrity%20is%20set%20of,NULL%20or%20invalid%20foreign%20keys
  .
* https://www.javatpoint.com/dbms-integrity-constraints#targetText=The%20entity%20integrity%20constraint%20states,than%20the%20primary%20key%20field
  .
* https://stackoverflow.com/questions/707874/differences-between-index-primary-unique-fulltext-in-mysql

### Books

* Chris Fehily SQL Visual QuickStart Guide 2008
* [about.com list](http://databases.about.com/od/reviews/tp/sqlbooks.htm)

### Knowledge

You can set the root password by typing this:

```
# mysqladmin -u root password 'new-password'
```

You can then login by typing this:

```
# mysql -u root –p
```

## mysql

```
# can't connect error 
sudo service mysql start
```

Then you'll be prompted to provide the password you specified earlier.

You also might want to delete the anonymous user in the User's table. The default configuration of MySQL allows any user
access to the system without providing a username or password.

Delete the user by typing this:

```
# mysql -u root –p
mysql> use mysql
mysql> delete from user where User='';
mysql> quit
```

### [Many SQL Commands](http://www.pantz.org/software/mysql/mysqlcommands.html)

## Chris Fehily SQL visual Quick start

### Primary Keys

Required, Unique, simple or composite, not null,stable(if deleted isn't reused), minimal.

**Tips**

```
primary key
```

### Foreign Keys

* Table which contains the foreign key is referencing or child table
* Referential Integrity: foreign-key values are restricted to existing parent-key values (no orphan rows allowed to be
  created)
* self referencing (`manager_id to employee_id`)

### Normalization

* Lossless decomposition ensures that table splitting doesn’t cause information loss.
* dependency-preserving decomposition ensures that relationships aren’t lost.

**1NF**

* Columns should be atomic (no authors={au1,au2,au3})
* has no repeating groups (author1, author2, author3)
* this should be solved by having a new table

**2NF**

* Partial Dependency is bad (when a column depends on one of composite keys)
* Full dependency is ok when column depends on both composite keys

**3NF**
A table contains a *transitive dependency* if a nonkey column’s value determines another nonkey column’s value.

In 3NF tables, non-key columns are mutually independent and dependent on only primary-key column(s).

For each nonkey column, ask, “Can I determine a nonkey column value if I know any other nonkey column value?” A no
answer means that the column is not transitively dependent (good); a yes answer means that the column whose value you
can determine is transitively dependent on the other column (bad).

### Denormalization

The increased number of tables that normalization generates might sway you to denormalize your database to speed
queries (because having fewer tables reduces computationally expensive joins and disk I/O). This common technique trades
off data integrity for performance and presents a few other problems. A denormalized database:
◆ Usually is harder to understand than a normalized one ◆ Usually makes retrievals faster but updates slower ◆ Increases
the risk of inserting inconsistent data ◆ Might improve the performance of some database applications but hurt that of
others (because users’ table-access patterns change over time)

## Chapter 4

* The WHERE clause is evaluated before the SELECT clause.

## Chapter 5

* ||
* substring(from 1 for 3)
* upper()
* trim()
* character_length()
* position()
* cast(bla as integer)
* case bla when expr then bla end from ...
* coalesce()
* nullif()

## Chapter 6

* min()
* max()
* sum()
* avg()
* count()

Aggregate functions (except COUNT(*)) ignore nulls. If an aggregation requires that you account for nulls, you can
replace each null with a specified value by using COALESCE():

```
SELECT AVG(COALESCE(sales,0))
AS AvgSales
FROM titles
WHERE type = 'biography';
```

aggr_fun(all|distinct expr)





