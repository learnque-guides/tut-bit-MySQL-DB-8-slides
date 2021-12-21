# The IF . . . ELSE flow element

You use the IF . . . ELSE element to control the flow of your code based on the result of a predicate. You specify a statement or statement block that is executed if the predicate is TRUE, and optionally a statement or statement block that is executed if the predicate is FALSE.

```sql
IF YEAR(NOW()) <> YEAR(DATE_ADD(NOW(), INTERVAL 1 DAY)) THEN
    SELECT 'Today is the last day of the year.' AS ``;
ELSE
    SELECT 'Today is not the last day of the year.' AS ``;
END IF;
```

---

```sql
IF YEAR(NOW()) <> YEAR(DATE_ADD(NOW(), INTERVAL 1 DAY)) THEN
    SELECT 'Today is the last day of the year.' AS ``;
ELSEIF MONTH(NOW()) <> MONTH(DATE_ADD(NOW(), INTERVAL 1 DAY)) THEN
    SELECT 'Today is the last day of the month but not the last day of the year.' AS ``;
ELSE
    SELECT 'Today is not the last day of the month.' AS ``;
END IF;
```

