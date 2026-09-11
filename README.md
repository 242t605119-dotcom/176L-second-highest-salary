# LeetCode 176 - Second Highest Salary

## Problem

Write a SQL query to find the **second highest distinct salary** from the `Employee` table.

If there is no second highest salary, return `NULL`.

## Approach

First, find the highest salary using:

```sql
MAX(salary)
```

Then exclude that salary using:

```sql
WHERE salary < (SELECT MAX(salary) FROM Employee)
```

Finally, find the maximum salary from the remaining values.

This gives the **second highest distinct salary**.

## SQL Query

```sql
SELECT MAX(salary) AS SecondHighestSalary
FROM Employee
WHERE salary < (
    SELECT MAX(salary)
    FROM Employee
);
```

## Example

### Employee

| id | salary |
| -- | -----: |
| 1  |    100 |
| 2  |    200 |
| 3  |    300 |

Highest salary = `300`

Second highest salary = `200`

### Output

| SecondHighestSalary |
| ------------------: |
|                 200 |

## Important Case

If the table contains only one distinct salary, there is no second highest salary.

The query returns:

```text
NULL
```

## Key Concepts

* SQL
* `MAX()`
* Subquery
* `WHERE`
* Distinct salary handling
* `NULL`

## What I Learned

This problem helped me understand how a subquery can be used to find the maximum value first and then find the next highest value.

Using `MAX()` again after excluding the highest salary also handles duplicate salaries correctly.

## LeetCode Details

* **Problem:** 176
* **Title:** Second Highest Salary
* **Language:** SQL
* **Difficulty:** Medium

## Author

T.Nandhini
