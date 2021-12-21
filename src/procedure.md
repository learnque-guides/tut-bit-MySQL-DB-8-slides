# Stored procedures

Stored procedures are routines that encapsulate code. They can have input and output parameters, they can return result sets of queries, and they are allowed to have side effects. Not only can you modify data through stored procedures, you can also apply schema changes through them.

* Stored procedures encapsulate logic. 
* Stored procedures give you better control of security. You can grant a user permissions to execute the procedure without granting the user direct permissions to perform the underlying activities.
* You can incorporate all error-handling code within a procedure, silently taking corrective action where relevant.
* Stored procedures give you performance benefits.


Syntax:

```sql
CREATE
    [OR REPLACE]
    [DEFINER = { user | CURRENT_USER | role | CURRENT_ROLE }]
    PROCEDURE sp_name ([proc_parameter[,...]])
    [characteristic ...] routine_body

proc_parameter:
    [ IN | OUT | INOUT ] param_name type

type:
    Any valid MariaDB data type

characteristic:
    LANGUAGE SQL
  | [NOT] DETERMINISTIC
  | { CONTAINS SQL | NO SQL | READS SQL DATA | MODIFIES SQL DATA }
  | SQL SECURITY { DEFINER | INVOKER }
  | COMMENT 'string'

routine_body:
    Valid SQL procedure statement
```

```sql
DELIMITER $$

CREATE OR REPLACE PROCEDURE getNumberOfCustomers (OUT number_of_customers INT)
 BEGIN
  SELECT COUNT(1) INTO number_of_customers FROM Customers;
 END;
$$

DELIMITER ;

CALL simpleproc(@a);

SELECT @a AS number_of_customers;
```
