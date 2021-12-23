# SIGNAL - error handling

*SIGNAL* empties the diagnostics area and produces a custom error. This statement can be used anywhere, but is generally useful when used inside a stored program. When the error is produced, it can be caught by a *HANDLER*. If not, the current stored program, or the current statement, will terminate with the specified error.

```sql
DELIMITER $$

CREATE PROCEDURE p()
BEGIN
  DECLARE EXIT HANDLER FOR SQLEXCEPTION
  SIGNAL SQLSTATE VALUE '99999'
    SET MESSAGE_TEXT = 'An error occurred';
  DROP TABLE no_such_table;
END;
$$

DELIMITER ;

CALL p();
```