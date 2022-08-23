### System Catalogs

1) A DBMS stores meta-data about databases in its internal catalogs.

> - Tables, Columns, Indexes, Views
> - Users, Permissions
> - Internal Statistics

2) Almost every DBMS stores their database catalog in itself.

> - Wrap object abstraction around tuples
> - Specialized code for "bootstrapping" catalog tables. <= ?

3) You can query the DBMS's internal INFORMATION_SCHEMA catalog to get info about the database.

> - ANSI standard set of readonly views that provide info about all of the tables views columns, and prcedures in a database.
> - Most of them also provide their own version of shortcuts (e.g., "\d" for Postgres)
