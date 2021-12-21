# LEAVE statement

This statement is used to exit the flow control construct that has the given label. The label must be in the same stored program, not in a caller procedure. LEAVE can be used within BEGIN ... END or loop constructs (LOOP, REPEAT, WHILE).

```sql
CREATE OR REPLACE PROCEDURE proc(IN p TINYINT)
`whole_proc`:
BEGIN
   SELECT 1;
   IF p < 1 THEN
      LEAVE `whole_proc`;
   END IF;
   SELECT 2;
END;

CALL proc(0);
```