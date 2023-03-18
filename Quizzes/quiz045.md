# Quiz 045

![Screen Shot 2023-03-18 at 16 33 53](https://user-images.githubusercontent.com/111895127/226091948-4e653ff6-f780-4be8-9131-d7aab584f083.png)

## Create the UML diagram
![Blank diagram](https://user-images.githubusercontent.com/111895127/226092775-23107e86-c72f-4d82-b501-6ebb0070ed97.png)

## Create the SQL queries to find the responsible for the fraudulent transaction

```.py
SELECT
  CASE
    WHEN total_deposit - total_withdraw != balance THEN 'bad'
    ELSE 'good'
  END AS 'Status',
  total_deposit,
  total_withdraw,
  balance,
  account_id
FROM (
  SELECT
    SUM(amount) AS total_deposit,
    account_id AS a_d
  FROM transactions
  WHERE transaction_type = 'deposit'
  GROUP BY account_id
),
(
  SELECT
    SUM(amount) AS total_withdraw,
    account_id AS a_w
  FROM transactions
  WHERE transaction_type = 'withdraw'
  GROUP BY account_id
),
accounts
WHERE a_d = a_w
  AND a_d = accounts.account_id;
```
![Screen Shot 2023-03-18 at 16 52 19](https://user-images.githubusercontent.com/111895127/226092911-335f18d4-4c4b-4a0f-84ef-893f5da208b8.png)

## What is the name of the customer and the problem that resulted in the bankruptcy of the bank?
```.py
SELECT customers.first_name, customers.last_name, accounts.account_id
FROM customers
JOIN accounts
ON customers.customer_id = accounts.customer_id
WHERE accounts.account_id IN (12, 13, 15, 17, 19);
```
![Screen Shot 2023-03-18 at 16 53 46](https://user-images.githubusercontent.com/111895127/226092962-83035f2a-fb4d-49e9-ae90-9a955c46f0ec.png)
