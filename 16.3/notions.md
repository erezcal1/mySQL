# Notions

- DB - a collection on tables

- Table - A collection on cols and rows that contains the specific information

- Col - the name of the values that will be saved under this cols

- Row - An information for on cols for example: USER

- PK - a specific key (primary key)

- FK - A connection to the PK from another table (foreign key)

- Query - A collation of orders that we will be using to make changes to the DB

- DRL - taking/redoing data. Start with Select

- DML - save/delete/update

- DDL - table settings

- DCL - giving access

- langues - DRL, DML, DDL, CDL

#### Data base for workers, costumers, orders, products:

- workers: idWorker(PK), name, surname
- clients: idClient(PK), name, surname, address, phone
- items: idItem(PK), name, price
- **orders: _idOrder(PK), idClient(FK), idWorker(FK), idItem(FK),_ date, quantity**
