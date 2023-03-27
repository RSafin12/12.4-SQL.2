# 12.4-SQL.2

## Задание 1
```
SELECT s.store_id, CONCAT(staff.first_name, ' ', staff.last_name) AS worker, staff_id,  c2.city, COUNT(c.customer_id)
FROM store s
INNER JOIN staff ON s.store_id = staff.store_id
INNER JOIN address a  ON staff.address_id = a.address_id
INNER JOIN city c2 ON a.city_id = c2.city_id
INNER JOIN customer c ON s.store_id = c.store_id
GROUP BY s.store_id, worker, staff_id, c2.city
HAVING COUNT(c.customer_id) > 300;
```
## Задание 2
```
SELECT COUNT(film_id)
FROM film f
WHERE `length`  > (SELECT AVG(`length`) FROM film f);
```

## Задание 3
```
SELECT DATE_FORMAT(payment_date, '%M,%Y')  AS `Month of the date`, SUM(amount) AS Max_Sum, COUNT(r.rental_id) AS Rent_per_month
FROM payment p
INNER JOIN rental r ON p.rental_id = r.rental_id
GROUP BY `Month of the date`
Order by Max_Sum DESC LIMIT 1
```

## Задание 4
```
SELECT p.staff_id, CONCAT(s.first_name, ' ', s.last_name) as worker, COUNT(payment_id),
CASE
	WHEN COUNT(payment_id) > 8000 THEN 'Yes'
	WHEN COUNT(payment_id) < 8000 THEN 'NO'
	ELSE 'equal'
END AS prem
FROM payment p
INNER JOIN staff s ON p.staff_id = s.staff_id
GROUP BY p.staff_id;
```
