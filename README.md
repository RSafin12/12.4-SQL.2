# 12.4-SQL.2

## Задание 1
```
SELECT s.store_id, CONCAT(staff.first_name, ' ', staff.last_name) AS worker, staff_id,  c2.city, MAX(c.customer_id)
FROM store s
INNER JOIN staff ON s.store_id = staff.store_id
INNER JOIN address a  ON staff.address_id = a.address_id
INNER JOIN city c2 ON a.city_id = c2.city_id
INNER JOIN customer c ON s.store_id = c.store_id
GROUP BY s.store_id, worker, staff_id, c2.city
HAVING MAX(c.customer_id) > 300;
```
## Задание 2
```
SELECT COUNT(film_id)
FROM film f
WHERE `length`  > (SELECT AVG(`length`) FROM film f);
```

## Задание 3
```
SELECT MONTH(CAST(payment_date as DATE)) as Месяц, MAX(amount) AS Max_Sum, COUNT(r.rental_id) AS Rent_per_month
FROM payment p
INNER JOIN rental r ON p.rental_id = r.rental_id
GROUP BY Месяц
HAVING Max_Sum = (SELECT MAX(amount) FROM payment p);

```
