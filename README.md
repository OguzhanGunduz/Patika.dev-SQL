# Patika.dev-SQL
Patika.dev SQL HomeWorks

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

```SQL
```

```SQL
```

```SQL
```
