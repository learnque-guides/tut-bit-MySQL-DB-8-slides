# Stored function

* The purpose of a user-defined function (UDF) or stored function is to encapsulate logic that calculates something, possibly based on input parameters, and return a result.
* User defined function can return only scalar value (single value).
* User defined function must not have side effects.

Syntax:

```sql
CREATE [OR REPLACE]
    [DEFINER = {user | CURRENT_USER | role | CURRENT_ROLE }]
    [AGGREGATE] FUNCTION [IF NOT EXISTS] func_name ([func_parameter[,...]])
    RETURNS type
    [characteristic ...]
    RETURN func_body


func_parameter:
    param_name type


type:
    Any valid MariaDB data type


characteristic:
    LANGUAGE SQL
  | [NOT] DETERMINISTIC
  | { CONTAINS SQL | NO SQL | READS SQL DATA | MODIFIES SQL DATA }
  | SQL SECURITY { DEFINER | INVOKER }
  | COMMENT 'string'


func_body:
    Valid SQL procedure statement
```

Example of function that return last order date for customer:

```sql
DELIMITER $$
CREATE FUNCTION last_customer_order_date (custid INT) RETURNS INT
BEGIN
    RETURN (SELECT MAX(orderdate) FROM Orders AS O WHERE O.custid = custid);
END;
$$

DELIMITER ;

SELECT last_customer_order_date(43);
```
Let's look at more complicated example.