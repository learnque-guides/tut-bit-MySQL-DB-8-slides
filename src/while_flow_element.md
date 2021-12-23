# The WHILE flow element

* SQL provides the WHILE element, which you can use to execute code in a loop. 
* The WHILE element executes a statement or statement block repeatedly while the predicate you specify after the WHILE keyword is TRUE. When the predicate is FALSE, the loop terminates.

```sql
DELIMITER $$
CREATE OR REPLACE PROCEDURE dowhile(OUT result INT)
BEGIN
  DECLARE v1 INT DEFAULT 5;
  WHILE v1 > 0 DO
    SET v1 = v1 - 1;
  END WHILE;
  SET result = v1;
END;
$$

DELIMITER $$

CALL dowhile(@result);
SELECT @result AS v1;
```

* If at some point in the loop's body you want to break out of the current loop and proceed to execute the statement that appears after the loop's body, use the LEAVE command with label.

```sql
DELIMITER $$

CREATE OR REPLACE PROCEDURE dowhile(OUT result INT)
BEGIN
  DECLARE v1 INT DEFAULT 5;
  myloop: WHILE v1 > 0 DO
    IF v1 = 3 THEN
        LEAVE myloop; -- similar to BREAK
    END IF;
    SET v1 = v1 - 1;
  END WHILE;
  SET result = v1;
END;
$$

CALL dowhile(@result);
SELECT @result AS v1;
```
