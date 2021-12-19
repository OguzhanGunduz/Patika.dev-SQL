# Patika.dev-SQL
Patika.dev SQL HomeWorks


```SQL
-----------------------
SELECT name FROM STUDENTS
WHERE Marks > 75
ORDER BY RIGHT(name, 3), id ASC;  --right function
-----------------------
SELECT CITY, LENGTH(CITY) FROM STATION  -- number of characters in the name
ORDER BY LENGTH(CITY), CITY
LIMIT 1;

--Hackerrank = Type of Triangle
--This is good example
SELECT CASE 
WHEN A + B <= C OR A + C <= B OR B + C <= A THEN 'Not A Triangle' 
WHEN A = B AND B = C THEN 'Equilateral' 
WHEN A = B OR B = C OR A = C THEN 'Isosceles' 
ELSE 'Scalene' 
END 
FROM TRIANGLES;

--Hackerrank = The Blunder
SELECT  CEIL(AVG(Salary-REPLACE(Salary, '0',''))) FROM EMPLOYEES; --round up to
--Hackerrank = top earners
SELECT MAX(months*salary), COUNT(*) FROM Employee
WHERE (months*salary) = (SELECT MAX(SALARY*MONTHS) FROM EMPLOYEE);
---------------------
```
## HomeWork 1

* Sort the data in the title and description columns in the film table.

```SQL
SELECT title, description FROM film;
```

* Sort the data in all columns in the film table with the movie length greater than 60 AND less than 75. 

```SQL
SELECT * FROM film 
WHERE length > 60 AND length < 75;
```

* Sort the data in all columns in the film table with rental_rate 0.99 AND replacement_cost 12.99 OR 28.99. 
```SQL
SELECT * FROM film
WHERE rental_rate > 0.99 AND replacement_cost > 12.99 OR replacement_cost = 28.99;
```

* What is the value in the last_name column of the customer whose value is 'Mary' in the first_name column of the customer table?

```SQL
SELECT last_name FROM customer
WHERE first_name = 'Mary';
```

* Rank the data in the film table that DOESN'T have a length greater than 50, and also a rental_rate of  not equal 2.99 or 4.99. 

```SQL
SELECT * FROM film
WHERE NOT (length > 50 AND rental_rate = 2.99 OR rental_rate = 4.99);
```

## HomeWork 2

* Sort the data in all columns in the film table provided that the replacement cost value is greater than 12.99, equal and less than 16.99 (Use BETWEEN - AND structure.) 

```SQL
SELECT * FROM film 
WHERE  replacement_cost BETWEEN 12.99 AND 16.99;
```

* Sort the data in the first_name and last_name columns in the actor table provided that first_name is 'Penelope' or 'Nick' or 'Ed'. (Use the IN operator.)

```SQL
SELECT   first_name, last_name FROM actor
WHERE  first_name IN ('Penelope','Nick','Ed');
```

* Sort the data in all columns in the film table with rental_rate 0.99, 2.99, 4.99 AND replacement_cost 12.99, 15.99, 28.99. (Use the IN operator.)

```SQL
SELECT * FROM film
WHERE rental_rate IN (0.99,2.99,4.99) AND replacement_cost IN (12.99,15.99,28.99);
```

## HomeWork 3

* List the country names in the country column of the country table, starting with the 'A' character and ending with the 'a' character. 

```SQL
SELECT * FROM country
WHERE country LIKE ('A%a');
```

* List the country names in the country column of the country table, consisting of at least 6 characters and ending with the 'n' character. 

```SQL
SELECT * FROM country
WHERE country LIKE('_____%n');
```

* In the title column of the film table, list the film names containing at least 4 'T' characters, regardless of upper or lower case letters. 

```SQL
SELECT * FROM film 
WHERE title ILIKE ('%T%T%T%T%');
```

* From the data in all the columns in the film table, sort the data that starts with the title 'C' character, has a length greater than 90 and a rental_rate of 2.99.

```SQL
SELECT * FROM film
WHERE title LIKE 'C%' AND length > 90 AND rental_rate = 2.99;
```

## HomeWork 4

* Sort the different values in the replacement_cost column in the film table.

```SQL
SELECT DISTINCT replacement_cost FROM  film
```

* How many different data are there in the replacement_cost column in the film table?

```SQL
SELECT COUNT(DISTINCT replacement_cost) FROM  film;
```

* How many of the film titles(title) in the film table start with the character T and at the same time the rating is equal to 'G'? 

```SQL
SELECT * FROM  film 
WHERE title LIKE 'T%' AND rating = 'G'
```

* How many of the country names (country) in the country table consist of 5 characters?

```SQL
SELECT COUNT(*)FROM country 
WHERE country LIKE '_____';
```

* How many of the city names in the city table end with the character 'R' or r? 

```SQL
SELECT COUNT(*) FROM city 
WHERE city ILIKE '%R';
```

## HomeWork 5
* film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.

```SQL
SELECT * FROM film
WHERE title LIKE '%n'
ORDER BY length DESC
LIMIT 5;
```

* film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci(6,7,8,9,10) 5 filmi(6,7,8,9,10) sıralayınız.

```SQL
SELECT * FROM film
WHERE title LIKE '%n'
ORDER BY length ASC
OFFSET 5
LIMIT 5;
```
* customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.

```SQL
SELECT * FROM customer
WHERE store_id = 1
ORDER BY last_name DESC
LIMIT 4;
```

## HomeWork 6 

* What is the average of the values in the rental_rate column in the film table? 

```SQL
SELECT AVG(rental_rate) FROM film;
-------------------------------------------------------
SELECT ROUND(AVG(rental_rate) , 3) FROM film; -- Mean value with 3 digit
```

* How many of the films in the film table start with the character 'C'? 

```SQL
SELECT COUNT(*) FROM film 
WHERE title LIKE 'C%';
```

* How many minutes is the longest (length) film with rental_rate equal to 0.99 among the films in the film table? 

```SQL
SELECT length FROM film
WHERE rental_rate = 0.99
ORDER BY length DESC
LIMIT 1;
--------------------------------------------------
SELECT max(length) FROM film
WHERE rental_rate = 0.99;    -- They are same output
```

* How many different replacement_cost values are there for the films longer than 150 minutes in the film table?

```SQL
SELECT COUNT(DISTINCT(replacement_cost) FROM film
WHERE length > 150;
```

## HomeWork 7

* Group the films in the film table according to their rating values.

```SQL
SELECT rating, COUNT(*) FROM film
GROUP BY rating;
```

* When we group the films in the film table according to the replacement_cost column, list the replacement_cost value with more than 50 films and the corresponding number of films.

```SQL
SELECT replacement_cost , COUNT(*) FROM film
GROUP BY replacement_cost
HAVING COUNT(*) > 50;
```

* What are the number of customers corresponding to the store_id values in the customer table?

```SQL
SELECT store_id, COUNT(*) FROM customer
GROUP BY store_id;
```

* After grouping the city data in the city table according to the country_id column, share the country_id information with the highest number of cities and the number of cities. 

```SQL
SELECT country_id, COUNT(city) FROM city
GROUP BY country_id
ORDER BY COUNT(city) DESC
LIMIT 1;
```

## HomeWork 8

* 

```SQL
CREATE TABLE employee (
	id SERIAL PRIMARY KEY,
	name VARCHAR(50),
	birthday DATE,
	email VARCHAR(100)
```

*

```SQL
insert into employee (id, name, email, birthday) values (1, 'Waite', 'wslack0@youtube.com', '1800-07-22');
insert into employee (id, name, email, birthday) values (2, 'Beltran', 'bcawkill1@upenn.edu', '0593-09-20');
insert into employee (id, name, email, birthday) values (3, 'Astrid', 'abrimman2@blogs.com', '1823-08-10');
insert into employee (id, name, email, birthday) values (4, 'Cassondra', 'cjorio3@usgs.gov', '0909-10-12');
insert into employee (id, name, email, birthday) values (5, 'Barnard', 'bzisneros4@qq.com', '1779-03-26');
insert into employee (id, name, email, birthday) values (6, 'Herbert', 'hbeverstock5@imdb.com', '1615-04-24');
insert into employee (id, name, email, birthday) values (7, 'Aurilia', 'arodrigo6@smugmug.com', '1670-09-01');
insert into employee (id, name, email, birthday) values (8, 'Hermie', 'hjeannesson7@earthlink.net', '1369-06-14');
insert into employee (id, name, email, birthday) values (9, 'Beverie', 'bmcsperrin8@php.net', '1009-12-27');
insert into employee (id, name, email, birthday) values (10, 'Cathyleen', 'chorley9@amazon.com', '1357-03-23');
insert into employee (id, name, email, birthday) values (11, 'Berna', 'bcrusta@microsoft.com', '0802-10-26');
insert into employee (id, name, email, birthday) values (12, 'Collie', 'cstanbrob@dot.gov', '1240-09-18');
insert into employee (id, name, email, birthday) values (13, 'Lamont', 'lroderighic@eepurl.com', '1632-08-16');
insert into employee (id, name, email, birthday) values (14, 'Vernon', 'vhebblewhited@businessweek.com', '1708-02-01');
insert into employee (id, name, email, birthday) values (15, 'Merissa', 'mmacaskiee@zimbio.com', '1659-11-02');
insert into employee (id, name, email, birthday) values (16, 'Felike', 'farchboldf@github.io', '1218-10-21');
insert into employee (id, name, email, birthday) values (17, 'Ediva', 'eshipleyg@pinterest.com', '0427-04-21');
insert into employee (id, name, email, birthday) values (18, 'Vanni', 'vsomerseth@discuz.net', '0841-04-27');
insert into employee (id, name, email, birthday) values (19, 'Homere', 'hhalleyi@goo.gl', '1143-10-21');
insert into employee (id, name, email, birthday) values (20, 'Haleigh', 'hdouganj@kickstarter.com', '0660-12-01');
insert into employee (id, name, email, birthday) values (21, 'Edgard', 'eashwellk@about.com', '0218-07-19');
insert into employee (id, name, email, birthday) values (22, 'Brendon', 'bretallackl@noaa.gov', '1490-06-05');
insert into employee (id, name, email, birthday) values (23, 'Lauritz', 'lblydenm@is.gd', '0989-03-26');
insert into employee (id, name, email, birthday) values (24, 'Maurizia', 'mpatisn@bigcartel.com', '1578-04-26');
insert into employee (id, name, email, birthday) values (25, 'Teresina', 'tvaeno@ezinearticles.com', '0628-02-01');
insert into employee (id, name, email, birthday) values (26, 'Stefania', 'shaizeldenp@is.gd', '1253-11-27');
insert into employee (id, name, email, birthday) values (27, 'Anstice', 'avanyukhinq@cornell.edu', '0678-03-03');
insert into employee (id, name, email, birthday) values (28, 'Cam', 'csorleyr@answers.com', '1292-01-05');
insert into employee (id, name, email, birthday) values (29, 'Cosetta', 'cgilbeys@wix.com', '0269-01-14');
insert into employee (id, name, email, birthday) values (30, 'Rana', 'rcottelt@yahoo.co.jp', '1451-12-18');
insert into employee (id, name, email, birthday) values (31, 'Vincents', 'vtextonu@sfgate.com', '1832-08-30');
insert into employee (id, name, email, birthday) values (32, 'Emelina', 'ecoulsenv@ucla.edu', '0998-04-17');
insert into employee (id, name, email, birthday) values (33, 'Lorant', 'lgainsburghw@linkedin.com', '1201-09-22');
insert into employee (id, name, email, birthday) values (34, 'Cristin', 'cweavingx@macromedia.com', '0340-11-12');
insert into employee (id, name, email, birthday) values (35, 'Marigold', 'mbispy@epa.gov', '1334-11-30');
insert into employee (id, name, email, birthday) values (36, 'Daryl', 'dcookmanz@unblog.fr', '0955-12-18');
insert into employee (id, name, email, birthday) values (37, 'Mitchel', 'mrawet10@nationalgeographic.com', '0525-04-01');
insert into employee (id, name, email, birthday) values (38, 'Efrem', 'elob11@blinklist.com', '1627-11-08');
insert into employee (id, name, email, birthday) values (39, 'Billye', 'bnarrie12@mit.edu', '1827-12-20');
insert into employee (id, name, email, birthday) values (40, 'Erroll', 'efranchioni13@mlb.com', '1788-02-12');
insert into employee (id, name, email, birthday) values (41, 'Mella', 'mmewett14@foxnews.com', '0434-04-09');
insert into employee (id, name, email, birthday) values (42, 'Rakel', 'rdyshart15@sohu.com', '0461-07-15');
insert into employee (id, name, email, birthday) values (43, 'Modestia', 'mgilgryst16@google.ca', '1355-04-12');
insert into employee (id, name, email, birthday) values (44, 'Alec', 'abravey17@wikia.com', '0719-10-08');
insert into employee (id, name, email, birthday) values (45, 'Althea', 'ahubberstey18@cdc.gov', '0786-11-30');
insert into employee (id, name, email, birthday) values (46, 'Brandice', 'bblampey19@paginegialle.it', '1860-09-22');
insert into employee (id, name, email, birthday) values (47, 'Elysha', 'emunnery1a@independent.co.uk', '0847-03-10');
insert into employee (id, name, email, birthday) values (48, 'Loise', 'llevet1b@about.me', '1319-01-04');
insert into employee (id, name, email, birthday) values (49, 'Giffie', 'gbennedsen1c@posterous.com', '0875-12-18');
insert into employee (id, name, email, birthday) values (50, 'Vergil', 'vkincey1d@1688.com', '0772-04-01');
```

*

```SQL
UPDATE employee
SET name = 'KEMAL', email = 'kemal@kemal.com', birthday ='1200-4-5'
WHERE id = 10;
--------------------------------------------------------------------------
DELETE FROM employee
WHERE id = 13;
```

## HomeWork 9

*

```SQL
SELECT city, country FROM city
INNER JOIN  country ON city.country_id = country.country_id;
```

*

```SQL
SELECT first_name, last_name, payment_id FROM customer
INNER JOIN payment ON customer.customer_id = payment.customer_id
```

*

```SQL
SELECT  first_name, last_name, rental_id FROM  customer
INNER JOIN  rental ON customer.customer_id = rental.customer_id
ORDER BY rental_id ASC;
```

## HomeWork 10

*

```SQL
SELECT city, country FROM city
LEFT  JOIN  country ON city.country_id = country.country_id;
```

*

```SQL
SELECT first_name, last_name, rental_id FROM customer
RIGHT JOIN payment ON customer.customer_id = payment.customer_id
ORDER BY rental_id ASC;
```

*

```SQL
SELECT first_name, last_name, rental_id FROM customer
FULL JOIN  rental ON customer.customer_id = rental.customer_id
ORDER BY rental_id ASC;
```

## HomeWork 11

* actor ve customer tablolarında bulunan first_name sütunları için tüm verileri sıralayalım.

```SQL
(SELECT a.first_name FROM actor as a)
UNION ALL -- If you dont want to repeat values then You should use UNION.
(SELECT c.first_name FROM customer as c);
```

* actor ve customer tablolarında bulunan first_name sütunları için kesişen verileri sıralayalım.

```SQL
(SELECT a.first_name FROM actor AS a)
INTERSECT
(SELECT c.first_name FROM customer AS c);
```

* actor ve customer tablolarında bulunan first_name sütunları için ilk tabloda bulunan ancak ikinci tabloda bulunmayan verileri sıralayalım.

```SQL
(SELECT a.first_name FROM actor AS a)
EXCEPT -- If you want to repeat values then You should use EXCEPT ALL.
(SELECT c.first_name FROM customer AS c)
```
