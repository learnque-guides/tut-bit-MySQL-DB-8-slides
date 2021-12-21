# FOR

Integer range FOR loop:

```sql
[begin_label:]
FOR var_name IN [ REVERSE ] lower_bound .. upper_bound
DO statement_list
END FOR [ end_label ]
```

Examples:

```sql
CREATE TABLE t1 (a INT);

DELIMITER $$

FOR i IN 1..3
DO
  INSERT INTO t1 VALUES (i);
END FOR;
$$

DELIMITER ;

SELECT * FROM t1;
```

Reverse integer range:

```sql
CREATE OR REPLACE TABLE t1 (a INT);

DELIMITER $$
FOR i IN REVERSE 4..12
    DO
    INSERT INTO t1 VALUES (i);
END FOR;
$$

DELIMITER ;

SELECT * FROM t1;
```

