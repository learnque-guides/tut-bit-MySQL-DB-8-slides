# Exercise 2

Write a procedure *FillDivisibleNumbers* that will fill table *divisible_numbers* with numbers from 0 to 100 that can be divided by some number.

For example, there are 25 numbers between 0 and 100 that are divisible by 4: *4, 8, 12, 16, 20, 24, 28, 32, 36, 40, 44, 48, 52, 56, 60, 64, 68, 72, 76, 80, 84, 88, 92, 96, 100.*

* You need to create a table *divisible_numbers* that have one property *number* of *INT* type;
* Create a procedure *FillDivisibleNumbers* that will accept *number* of *INT* type that will be used for checking if range from 0 to 100 is divisible by it.
* *CALL* procedure to get all divisible numbers from filled table *divisible_numbers*

By executing such statement:

```sql
CALL FillDivisibleNumbers(4);

SELECT `number` FROM `divisible_numbers`;
```

desired result is:

```
number
-------
4
8
12
16
20
24
28
32
36
40
44
48
52
56
60
64
68
72
76
80
84
88
92
96
100

25 record(s) affected
```


