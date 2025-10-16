# P1_RETAIL_SALES-
## 🧹 Data Cleaning

These help ensure your dataset is accurate, complete, and consistent:

### Missing & Invalid Values
- Which rows have missing values in critical columns like `age`, `quantity`, `price_per_unit`, or `total_sale`?
select * from retail_sales
where age is null
	or
	quantity is null
	or
	price_per_unit is null
	or
	total_sale is null;

- Are there any rows where `quantity * price_per_unit ≠ total_sale`? If so, how many?
select quantity*price_per_unit != total_sale
from retail_sales;

- Are there any duplicate `transactions_id` or identical rows?
select transactions_id,count(*) as count
from retail_sales
group by 1
order by count(*)>1;

- Are there any invalid or outlier values in `age` (e.g., negative, extremely high)?
select * from retail_sales
where age < 0;

- Are there any transactions with zero or negative `quantiy`, `price_per_unit`, or `total_sale`?
select * from retail_sales
where quantity < 0 or price_per_unit < 0 or total_sale < 0;
