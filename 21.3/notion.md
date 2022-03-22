# mySQL

## PAY ATTENTION TO WHERE!!!!!!

### Insert a line in mySQL table:

- INSERT INTO `table` (`column1`, `column2`) VALUES (`value1`, `value2`);

#### Example:

```sql
INSERT INTO clients
(
name,
lname,
address,
phone)
VALUES
(
'Itzik',
'Amrani Kala',
'Salame, Tel aviv',
'054-123456789');

SELECT * FROM shuki_ferrary.clients;
```

### Delete a line in mySQL table:

- DELETE FROM `orders` WHERE `idOrder` = 1;
  > `code` can be changed to what you need

#### class work:

- Delete the line where the number is: 054-876-543
  > DELETE FROM `orders` WHERE `number` = 054-876-543;

### Update a line in mySQL table:

- UPDATE `orders` SET `amount` = 3 WHERE `idOrder` = 1;

### Select a line in mySQL table:

- SELECT `col 1` FROM `orders` WHERE `idOrder` = 1;

- Show all data from table:
  > SELECT \* FROM `orders`;

### Where

- Where is optional condition
- If not written it will show all data from table

## AND - &&

- AND is optional condition
- Will show all data from table where both conditions are true

## OR - ||

- OR is optional condition
- Will show all data from table where one of the conditions is true (or both)

## ORDER BY

- ORDER BY is optional condition
- Will show the data in the order you want a-z and 0-n (asc - default) or z-a and n-0 (desc)

  ### Example:

  ```sql
  SELECT * FROM eshop.employees where status = 1 and city = 'Tel Aviv' order by firstname desc;
  ```

### Limit

- Limit is optional condition
- Will show the data in the number of lines you want

  `LIMIT 0, 10;`

  - skip 0 lines (default) and show until line 10

### Count

- Count the rows in a table
- SELECT COUNT(\*) as **_column name_** FROM `orders`;
  #### Example:
  ```sql
  SELECT count(*) as 'employees not working' FROM eshop.employees where status = 0;
  ```

### BETWEEN

- BETWEEN is optional condition
- Will show the data in the range you want
  - SELECT \* FROM `orders` WHERE `amount` BETWEEN `1` AND `3`;

### IN

- IN is optional condition
- Will show the data in the list you want
  - SELECT \* FROM `orders` WHERE `amount` IN (`1`, `2`, `3`);

### NOT

- NOT is optional condition
- Will show the data that don't match the condition
  - SELECT \* FROM `orders` WHERE `amount` NOT IN (`1`, `2`, `3`);

### Accumulation functions

- SUM, AVG, MIN, MAX, COUNT
  - SELECT `sum(amount)`, `avg(amount)`,` min(amount)` (smallest), `max(amount)`(biggest), `count(amount)`(counting the lines) FROM `orders`;
  #### Example: shows all the min payment in the DB
  ```sql
  select * from payment where amount = (select min(amount) from
  payment)
  ```

### CONCAT

- CONCAT is optional condition
- ````sql
  SELECT actor_id,
  concat(first_name, ' ', last_name) as 'Full Name'
  FROM sakila.actor```
  ````

### IF

- IF is optional condition
- ```sql
  SELECT \*, IF(active= 1, 'Active', 'Not Activ') FROM customer;
  ```
- if the condition ias true it will show the first value, if not it will show the second value

### CASE

```sql
SELECT *, case
 When length < (select avg(length) from film)
 THEN 'Short'
 WHEN length < ((select avg(length) from film) + 10) and length > ((select avg(length) from film) - 10)
 THEN 'normal'
 ELSE 'long'
end as 'timing'
FROM sakila.film;
```

### LIKE

- A% start with the a letter
- %A end with the a letter
- %A% contains the a letter
- A%A start and finish with the a letter

```sql
SELECT * FROM sakila.film WHERE title LIKE '%A%';
```
