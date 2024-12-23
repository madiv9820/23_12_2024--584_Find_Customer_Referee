# [584. Find Customer Referee](https://leetcode.com/problems/find-customer-referee?envType=study-plan-v2&envId=top-sql-50)

- ### Problem Understanding:
    You need to find the names of customers who were **not referred by the customer with `id = 2`**. The `referee_id` column indicates who referred each customer, and if `referee_id = 2`, then that customer was referred by the customer with `id = 2`.

- ### General Approach:
    1. **Identify Customers Not Referred by `id = 2`**:
        - The task is to exclude customers whose `referee_id` equals `2` from the result.
        - This can be done by applying a filter that checks if `referee_id` is **not equal to** `2` or is **null** (indicating they were not referred by anyone).

    2. **Select the Customer Names**:
        - After filtering out the customers referred by `id = 2`, you simply need to **select the `name` column** of the remaining customers.

- ### Key Steps:
    1. **Filter** the `Customer` table based on the condition `referee_id != 2` or `referee_id IS NULL`.
    2. **Select** the `name` column from the filtered data.
    3. **Return** the result as the list of customer names who were not referred by customer `id = 2`.

- ### Intuition for Each Framework:
    - **SQL**: Use a `WHERE` clause with the condition `referee_id != 2` (or `IS NULL` if needed).
    - **PySpark**: Use the `.filter()` method to apply the condition `df['referee_id'] != 2` (or `isNull()` for null values).
    - **Pandas**: Use boolean indexing to filter rows where `referee_id` is not equal to `2` or is `null`.

- ### Code Implementation
    - **SQL:**
        ```sql []
        SELECT name FROM Customer 
        WHERE referee_id != 2 OR referee_id IS NULL
        ```
    - **Pyspark:**
        ```python3 []
        def find_customer_referee(customer: pyspark.sql.dataframe.DataFrame) -> pyspark.sql.dataframe.DataFrame:
            customer_name = customer.filter((customer['referee_id'] != 2) | 
                                            (customer['referee_id']).isNull())\
                                    .select('name')
            return customer_name        
        ```
    - **Pandas:**
        ```python3 []
        def find_customer_referee(customer: pd.DataFrame) -> pd.DataFrame:
            customer_name = customer[(customer['referee_id'] != 2) | 
                                    (customer['referee_id'].isna())]\
                                    .name
            customer_name = pd.DataFrame(customer_name)
            return customer_name

        ```
        
- ### Common Points:
    - The task revolves around filtering data based on a condition (`referee_id != 2`).
    - The filtered data should be **projected** to return only the `name` of the customers.
    - The result is a list of customers who were **not referred by customer `id = 2`**.

- ### Conclusion:
    - **Filtering** is the primary operation here, and **selecting** specific columns follows once the filtering condition is applied.
    - The logic is consistent across all three tools (SQL, PySpark, Pandas), with differences only in syntax.
