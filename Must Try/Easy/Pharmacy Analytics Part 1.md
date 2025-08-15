---
Date: 2025-07-30
Difficulty: Easy
---
CVS Health is trying to better understand its pharmacy sales, and how well different products are selling. Each drug can only be produced by one manufacturer.

Write a query to find the top 3 most profitable drugs sold, and how much profit they made. Assume that there are no ties in the profits. Display the result from the highest to the lowest total profit.

**Definition:**

- `cogs` stands for Cost of Goods Sold which is the direct cost associated with producing the drug.
- Total Profit = Total Sales - Cost of Goods Sold

If you like this question, try out [Pharmacy Analytics (Part 2)](https://datalemur.com/questions/non-profitable-drugs)!

### `pharmacy_sales` Table:

|**Column Name**|**Type**|
|---|---|
|product_id|integer|
|units_sold|integer|
|total_sales|decimal|
|cogs|decimal|
|manufacturer|varchar|
|drug|varchar|

### `pharmacy_sales` Example Input:

|**product_id**|**units_sold**|**total_sales**|**cogs**|**manufacturer**|**drug**|
|---|---|---|---|---|---|
|9|37410|293452.54|208876.01|Eli Lilly|Zyprexa|
|34|94698|600997.19|521182.16|AstraZeneca|Surmontil|
|61|77023|500101.61|419174.97|Biogen|Varicose Relief|
|136|144814|1084258|1006447.73|Biogen|Burkhart|

### Example Output:

|**drug**|**total_profit**|
|---|---|
|Zyprexa|84576.53|
|Varicose Relief|80926.64|
|Surmontil|79815.03|

### Explanation:

Zyprexa made the most profit (of $84,576.53) followed by Varicose Relief (of $80,926.64) and Surmontil (of $79,815.3).

To find the top 3 most profitable drugs sold and their total profit, you can use the following SQL query:

```SQL
SELECT 
    drug,
    total_sales - cogs AS total_profit
FROM pharmacy_sales
ORDER BY total_profit DESC
LIMIT 3;
```

This query works as follows:

- **Calculate total profit**: The `total_sales - cogs` expression calculates the total profit for each drug.

- **Sort by total profit**: The ORDER BY clause sorts the results in descending order based on the total profit.

- **Limit to top 3**: The LIMIT clause limits the output to the top 3 most profitable drugs.

This query will return the name of each drug and its total profit, sorted from highest to lowest total profit. The result will match the example output:

| drug            | total_profit |
| --------------- | ------------ |
| Zyprexa         | 84576.53     |
| Varicose Relief | 80926.64     |
| Surmontil       | 79815.03     |
