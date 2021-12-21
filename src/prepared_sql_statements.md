# Prepared SQL statements

MySQL 8.0 and MariaDB 10.4 provides support for server-side prepared statements. This support takes advantage of the efficient client/server binary protocol. Using prepared statements with placeholders for parameter values has the following benefits:

* Less overhead for parsing the statement each time it is executed. Typically, database applications process large volumes of almost-identical statements, with only changes to literal or variable values in clauses such as WHERE for queries and deletes, SET for updates, and VALUES for inserts.

* Protection against SQL injection attacks. The parameter values can contain unescaped SQL quote and delimiter characters.

For creating a prepared statment you need to use syntax:

```sql
PREPARE stmt_name FROM preparable_stmt
```

For executing prepared statement you can use:

```sql
EXECUTE stmt_name
    [USING @var_name [, @var_name] ...]
```

For deallocating prepared statement you can use:

```sql
DEALLOCATE PREPARE stmt_name;
```

Example:

```sql
PREPARE stm FROM 'SELECT * FROM lessons.Orders WHERE orderid BETWEEN ? AND ?';
SET @a = 10248;
SET @b = 10250;
EXECUTE stm USING @a, @b;
```
