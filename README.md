# Домашнее задание к занятию "`SQL. Часть 1`" - `Стрекозов Владимир`

Задание можно выполнить как в любом IDE, так и в командной строке.  

### Задание 1
Получите уникальные названия районов из таблицы с адресами, которые начинаются на “K” и заканчиваются на “a” и не содержат пробелов.  
Запрос:  
`SELECT DISTINCT  district  FROM address WHERE district like 'K%a';`  
![](https://github.com/Svalker1989/SQL_Part1/blob/main/Z1.PNG)  

### Задание 2
Получите из таблицы платежей за прокат фильмов информацию по платежам, которые выполнялись в промежуток с 15 июня 2005 года по 18 июня 2005 года включительно и стоимость которых превышает 10.00.  
Запрос:  
`select payment_id,amount,payment_date from payment where amount > 10.00 and date(payment_date) BETWEEN '2005-06-15' and '2005-06-18';`  
![](https://github.com/Svalker1989/SQL_Part1/blob/main/Z2.PNG)  
### Задание 3
Получите последние пять аренд фильмов.  
Запрос:  
`select rental_date, customer_id, return_date from rental  order by rental_date desc limit 5;`  
![](https://github.com/Svalker1989/SQL_Part1/blob/main/Z3.PNG)  
Задание 4
Одним запросом получите активных покупателей, имена которых Kelly или Willie.  
Сформируйте вывод в результат таким образом:  
Все буквы в фамилии и имени из верхнего регистра переведите в нижний регистр,замените буквы 'll' в именах на 'pp'.  
Запрос:  
`select lower(first_name), replace(lower(last_name), 'll', 'pp'), active from customer where active=1 and last_name like 'kelly' or last_name like 'willis';`  
![](https://github.com/Svalker1989/SQL_Part1/blob/main/Z4.PNG)  
### Задание 5*
Выведите Email каждого покупателя, разделив значение Email на две отдельных колонки: в первой колонке должно быть значение, указанное до @, во второй — значение, указанное после @.  
Запрос:  
`select SUBSTRING_INDEX(email, '@', 1), SUBSTRING_INDEX(email, '@', -1) from customer`  
![](https://github.com/Svalker1989/SQL_Part1/blob/main/Z5.PNG)  

### Задание 6*
Доработайте запрос из предыдущего задания, скорректируйте значения в новых колонках: первая буква должна быть заглавной, остальные — строчными.  
Запрос:  
`select CONCAT(upper( left(SUBSTRING_INDEX(email, '@', 1) , 1)) , lower( SUBSTRING(SUBSTRING_INDEX(email, '@', 1) , 2 ))), CONCAT(upper( left(SUBSTRING_INDEX(email, '@', -1) , 1)) , lower( SUBSTRING(SUBSTRING_INDEX(email, '@', -1) , 2 )))  from customer;`  
![](https://github.com/Svalker1989/SQL_Part1/blob/main/Z6.PNG)  
