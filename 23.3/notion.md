# MYSQL

## SELECT GENERAL SKELETON

```sql
- SELECT
  - destinct
  - *, ...
  - FROM
  - WHERE
  - GROUP BY
  - HAVING
  - ORDER BY
  - LIMIT
```

### DISTINCT

- SELECT distinct district FROM address
- show only unique values
  - SELECT count(distinct district) as 'districts' FROM address;
  - count the number of unique values in the column

### GROUP BY

- group by will split then table into groups
- ```sql
  SELECT actor_id FROM film_actor group by actor_id;
  ```
  show all the actor_id in the table
- ```sql
  SELECT actor_id, count(\*) 'movies played in' FROM film_actor group by actor_id;
  ```

  if we want to count how many records are in each group

- ```sql
  SELECT if(active = 1, 'activ', 'disconected') as Status, count(\*) 'is or isn\'t activ' FROM customer group by active;
  ```

  show the number or active and non active customers

- ```sql
  SELECT staff_id, sum(amount) FROM payment group by staff_id;
  ```
  sum the amount of sales in each group

### HAVING

- Is a condition that is used to filter the results of a group by
  - ```sql
    SELECT rental_duration, avg(length) as avg_Leng
    FROM sakila.film
    group by rental_duration
    having avg_Leng > 115;
    ```

### NULL

- check if a column is null
  - ```sql
    SELECT * FROM customer where address_id is null;
    ```
- check if a column have a value
  - ```sql
    SELECT * FROM customer where address_id is not null;
    ```

### UNION

#### all of the columns must be identical

- UNION ALL - doesn't show identical rows
- used to connect to different tables
- ```sql
    SELECT * FROM customer
    UNION
    SELECT * FROM address;
  ```
  show all the customers and all the addresses

### INNER JOIN

- merge two tables

```sql
SELECT concat(actor.first_name, ' ', actor.last_name) as full_name, film.title FROM film_actor
INNER JOIN actor ON film_actor.actor_id = actor.actor_id
INNER JOIN film ON film.film_id = film_actor.film_id
#WHERE film_actor.actor_id = 1
```

### CLASS WORK

this code finds all the actors that played more then the average number of films

```sql
SELECT film_actor.actor_id, CONCAT(actor.first_name, ' ', actor.last_name) as full_name, COUNT(*) as avgfilms
	FROM film_actor
    INNER JOIN actor ON actor.actor_id = film_actor.actor_id
    GROUP BY film_actor.actor_id
    HAVING avgfilms >
		(SELECT
			AVG(avgfilms)
            FROM
				(SELECT
					actor_id,
                    COUNT(*) as avgfilms
                    FROM film_actor
                    GROUP BY actor_id)
                    AS avgtab)


#SELECT actor_id, COUNT(*) as avgfilms FROM film_actor GROUP BY actor_id
```
