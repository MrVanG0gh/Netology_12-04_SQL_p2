# Домашнее задание к занятию «SQL. Часть 2» - `Иншаков Владимир`

### Задание 1

Одним запросом получите информацию о магазине, в котором обслуживается более 300 покупателей, и выведите в результат следующую информацию: 
- фамилия и имя сотрудника из этого магазина;
- город нахождения магазина;
- количество пользователей, закреплённых в этом магазине.

### Решение 1

```
SELECT st.staff_id AS 'Номер сотрудника', CONCAT(st.first_name , ' ', st.last_name) AS 'Сотрудник', ci.city AS 'Город', COUNT(cus.customer_id) AS 'Количество покупателей'		
FROM sakila.store s
JOIN sakila.staff st on st.store_id = s.store_id 
JOIN sakila.customer cus on cus.store_id = s.store_id
JOIN sakila.address a on a.address_id = s.address_id 
JOIN sakila.city ci on ci.city_id = a.city_id 
GROUP BY st.staff_id, ci.city_id 
HAVING COUNT(cus.customer_id) > 300;
```
![Screenshot_1](https://github.com/MrVanG0gh/Netology_12-04_SQL_p2/blob/main/Screenshots/Screenshot_1.png)

---

### Задание 2

Получите количество фильмов, продолжительность которых больше средней продолжительности всех фильмов.

### Решение 2

```
SELECT COUNT(1) AS 'Количество фильмов'
FROM sakila.film f
WHERE f.`length` > (
	SELECT AVG(f.`length`)
	FROM sakila.film f
	)
```
![Screenshot_2](https://github.com/MrVanG0gh/Netology_12-04_SQL_p2/blob/main/Screenshots/Screenshot_2.png)

---

### Задание 3

Получите информацию, за какой месяц была получена наибольшая сумма платежей, и добавьте информацию по количеству аренд за этот месяц.

### Решение 3




---