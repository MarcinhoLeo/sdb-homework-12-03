# Домашнее задание к занятию "`SQL. Часть 1`" - `Гунба Леонардо`

### Задание 1

Получите уникальные названия районов из таблицы с адресами, которые начинаются на “K” и заканчиваются на “a” и не содержат пробелов.

```
SELECT DISTINCT city_id, city
From city
WHERE city Like 'K%a';

city_id|city        |
-------+------------+
    252|Kaduna      |
    253|Kakamigahara|
    256|Kamakura    |
    260|Kanazawa    |
    261|Kanchrapara |
    276|Koriyama    |
    277|Korla       |
    281|Ktahya      |
    287|Kuwana      |
```

### Задание 2

Получите из таблицы платежей за прокат фильмов информацию по платежам, которые выполнялись в промежуток с 15 июня 2005 года по 18 июня 2005 года включительно, и стоимость которых превышает 10.00.


```
По числам:

SELECT * from rental
WHERE rental_date BETWEEN '2005-06-15 00:00:00' and '2005-06-18 23:59:59';

Больше > 10 

SELECT * from payment
WHERE payment_date  BETWEEN '2005-06-15 00:00:00' and '2005-06-18 23:59:59' and amount > 10;

payment_id|customer_id|staff_id|rental_id|amount|payment_date       |last_update        |
----------+-----------+--------+---------+------+-------------------+-------------------+
       908|         33|       1|     1301| 10.99|2005-06-15 09:46:33|2006-02-15 22:12:36|
      7017|        260|       1|     2091| 10.99|2005-06-17 18:09:04|2006-02-15 22:14:58|
      8272|        305|       1|     2166| 11.99|2005-06-17 23:51:21|2006-02-15 22:15:47|
     12888|        477|       1|     2306| 10.99|2005-06-18 08:33:23|2006-02-15 22:19:46|
     13892|        516|       1|     1718| 10.99|2005-06-16 14:52:02|2006-02-15 22:20:47|
     14620|        544|       2|     1434| 10.99|2005-06-15 18:30:46|2006-02-15 22:21:35|
     15313|        572|       2|     1889| 10.99|2005-06-17 04:05:12|2006-02-15 22:22:22|
```

### Задание 3

Получите последние пять аренд фильмов.


```
SELECT rental_rate, title
from film
ORDER BY rental_rate DESC, title
Limit 5;

rental_rate|title           |
-----------+----------------+
       4.99|ACE GOLDFINGER  |
       4.99|AIRPLANE SIERRA |
       4.99|AIRPORT POLLOCK |
       4.99|ALADDIN CALENDAR|
       4.99|ALI FOREVER     |
```

### Задание 4

Одним запросом получите активных покупателей, имена которых Kelly или Willie.

Сформируйте вывод в результат таким образом:

* все буквы в фамилии и имени из верхнего регистра переведите в нижний регистр,
* замените буквы 'll' в именах на 'pp'.

```
SELECT (LOWER(first_name)),(LOWER(last_name)), email,
REPLACE (first_name, 'LL', 'PP')
from customer
WHERE first_name Like 'kel%' OR first_name = 'willie'

(LOWER(first_name))|(LOWER(last_name))|email                            |REPLACE (first_name, 'LL', 'PP')|
-------------------+------------------+---------------------------------+--------------------------------+
kelly              |torres            |KELLY.TORRES@sakilacustomer.org  |KEPPY                           |
willie             |howell            |WILLIE.HOWELL@sakilacustomer.org |WIPPIE                          |
willie             |markham           |WILLIE.MARKHAM@sakilacustomer.org|WIPPIE                          |
kelly              |knott             |KELLY.KNOTT@sakilacustomer.org   |KEPPY                           |

```
