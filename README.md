
# LeetCode Challenge D23
## Achievements
[![image.png](https://i.postimg.cc/nLnBcJfN/image.png)](https://postimg.cc/fVgJB1Lv)

This solution outperformed 89.87% of MySQL users on LeetCode according to runtime metrics and 100% according to memory metrics.


## Overview

Welcome to my LeetCode solution repository! This project addresses the coding challenge presented by [1084.  Sales Analysis III](https://leetcode.com/problems/sales-analysis-iii/). Below, you'll find details about the problem, my approach to solving it, and the implemented solution.

## Problem Statement
Write a solution to report the  **products**  that were  **only**  sold in the first quarter of  `2019`. That is, between  `2019-01-01`  and  `2019-03-31`  inclusive.

Return the result table in  **any order**.


**Example**

> **Input:**
> Product Table:
> | product_id | product_name | unit_price |
>|:----------:|:------------:|:----------:|
>|      1     |      S8      |    1000    |
>|      2     |      G4      |     800    |
>|      3     |    iPhone    |    1400    |
>
> Sales Table:
> | seller_id | product_id | buyer_id | sale_date  | quantity | price |    
>| :----------:|:----------:|:--------:|:----------:|:--------:|:-----:|        
>|  1         | 1          | 1        | 2019-01-21 | 2        | 2000  | 
>|  1         | 2          | 2        | 2019-02-17 | 1        | 800   | 
>|  2         | 2          | 3        | 2019-06-02 | 1        | 800   | 
>|  3         | 3          | 4        | 2019-05-13 | 2        | 2800  |
>
> **Output:**
> | product_id | product_name |
>|:----------:|:------------:|
>|      1     |      S8      |

> **Explanation** 
>The product with id 1 was only sold in the spring of 2019.
>The product with id 2 was sold in the spring of 2019 but was also sold after the spring of 2019.
>The product with id 3 was sold after spring 2019.
>We return only product 1 as it is the product that was only sold in the spring of 2019.

**Language Used**
> MySQL

**Difficulty**
> Easy

## Solution Overview

This SQL query uses a `LEFT JOIN` to combine the `Product` and `Sales` tables based on the `product_id`, ensuring all products are included in the result, even those without sales. The `WHERE` clause filters the results to include only products with sales between '2019-01-01' and '2019-03-31'. The `NOT EXISTS` subquery checks if there are no sales for the same product outside this date range, ensuring that the product was exclusively sold in the first quarter of 2019. 
This combination of `LEFT JOIN`, `WHERE`, and `NOT EXISTS` efficiently identifies such products. Alternatively, a `HAVING` clause with `GROUP BY` could achieve a similar result by grouping products and applying aggregate conditions to filter those exclusively sold in the specified quarter. The choice between these approaches depends on personal preference and the dataset's characteristics.
