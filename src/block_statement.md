# Block statement

* If you need to run more than one statement in some sections, you need to use a statement block. 
* You mark the boundaries of a statement block with the BEGIN and END keywords.

```sql
BEGIN NOT ATOMIC
  SELECT 'Im inside of block' AS ``;
END;
```