# 12.4-SQL.2

## Задание 1
SELECT s.store_id, CONCAT(staff.first_name, ' ', staff.last_name) AS worker, a.address, MAX(c.customer_id)
FROM store s
INNER JOIN staff ON s.store_id = staff.store_id
INNER JOIN address a  ON staff.address_id = a.address_id  
INNER JOIN customer c ON s.store_id = c.store_id
GROUP BY s.store_id, worker, a.address;
