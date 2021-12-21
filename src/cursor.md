# Cursor

A cursor is a structure that allows you to go over records sequentially, and perform processing based on the result.

* A cursor—a nonrelational result with order guaranteed among rows.
* For example, query with *ORDER BY* clause returns a so called cursor.
* SQL supports an object called cursor which you can use to process rows from a result of a query one at a time and in a requested order.

Disadvantages of cursor:

* When you use cursors you pretty much go against the relational model, which is based on set theory.
* The record-by-record manipulation done by the cursor has overhead. A certain extra cost is associated with each record manipulation by the cursor compared to set-based manipulation.
* With cursors, you write imperative solutions.

Working with a cursor generally involves the following steps:
* Declare the cursor based on a query (*DECLARE CURSOR*).
* Open the cursor (*OPEN*).
* Fetch attribute values from the first cursor record into variables (*FETCH*).
* As long as you haven’t reached the end of the cursor, loop through the cursor records.
* Close the cursor (*CLOSE*).

Let's look at example.