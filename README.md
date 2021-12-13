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











