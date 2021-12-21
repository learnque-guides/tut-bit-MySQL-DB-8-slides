# Triggers

* A trigger, as its name suggests, is a set of statements that run, or are triggered, when an event occurs on a table.
* A trigger is a special kind of stored procedure - one that cannot be executed explicitly. Instead, it’s attached to an event. Whenever the event takes place, the trigger fires and the trigger’s code runs.
* The event can be an INSERT, an UPDATE or a DELETE. The trigger can be executed BEFORE or AFTER the event.
* In the trigger’s code, you can access pseudo variables called NEW and OLD that contain the rows that were affected by the modification that caused the trigger to fire.
* In an INSERT trigger, only NEW.col_name can be used; there is no old row. In a DELETE trigger, only OLD.col_name can be used; there is no new row. In an UPDATE trigger, you can use OLD.col_name to refer to the columns of a row before it is updated and NEW.col_name to refer to the columns of the row after it is updated.
  
Simple trigger example:

```sql
CREATE TABLE animals
(
    id   mediumint(9) NOT NULL AUTO_INCREMENT,
    name char(30) NOT NULL,
    PRIMARY KEY (`id`)
);

CREATE TABLE animal_count
(
    animals int
);

INSERT INTO animal_count (animals)
VALUES (0);

-- --------------------------------------------

DELIMITER $$
CREATE TRIGGER increment_animal
    AFTER INSERT
    ON animals
    FOR EACH ROW
BEGIN
    UPDATE animal_count SET animal_count.animals = animal_count.animals + 1;
END;
$$

DELIMITER ;
```

You can use DROP, CREATE OR REPLACE statements with triggers as well.

Triggers can be used:
* Implementing auditing tables that tracks changes;
* Implementing column data validation logic;
* Implementing some business logic that should occur when recors is inserted or updated;
