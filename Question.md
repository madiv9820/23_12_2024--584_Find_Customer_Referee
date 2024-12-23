# [584. Find Customer Referee](https://leetcode.com/problems/find-customer-referee?envType=study-plan-v2&envId=top-sql-50)

**Type:** Easy <br>
**Topics:** Database <br>
**Companies:** Google, Microsoft, Meta, Bloomberg, Amazon, Apple, Adobe, Uber, Yahoo, tcs
<hr>

Table: `Customer`
```
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| id          | int     |
| name        | varchar |
| referee_id  | int     |
+-------------+---------+
In SQL, id is the primary key column for this table.
Each row of this table indicates the id of a customer, their name, and the id of the customer who referred them.
```

Find the names of the customer that are **not referred by** the customer with `id = 2`.

Return the result table in **any order**.

The result format is in the following example.
<hr>

### Examples
- **Example 1:** <br>
    - **Input:**
        ``` 
        Customer table:
        +----+------+------------+
        | id | name | referee_id |
        +----+------+------------+
        | 1  | Will | null       |
        | 2  | Jane | null       |
        | 3  | Alex | 2          |
        | 4  | Bill | null       |
        | 5  | Zack | 1          |
        | 6  | Mark | 2          |
        +----+------+------------+
        ```
    - **Output:** 
        ```
        +------+
        | name |
        +------+
        | Will |
        | Jane |
        | Bill |
        | Zack |
        +------+
        ```
<hr>

### Hints:
- Be careful of the NULL value