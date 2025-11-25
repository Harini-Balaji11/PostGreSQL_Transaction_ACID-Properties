# PostgreSQL Transaction Management and ACID Properties  
### CS623 Database Systems – Spring 2025  

**Author: Harini Balaji**

---

## Overview  
This project is a practical demonstration of how ACID properties work in PostgreSQL. I built a small inventory management system—products, depots, and stock levels—and used Python to perform different transactions, show commits and rollbacks, and observe how PostgreSQL maintains consistency using cascading constraints.

The intention was to go beyond theory and see how a database actually behaves during inserts, updates, deletes, and errors.

---

## What This Project Covers  
- Designing a relational schema with foreign keys  
- Applying cascading updates and deletes  
- Running transactions with commit and rollback  
- Using the `SERIALIZABLE` isolation level  
- Testing durability by validating committed results  
- Handling errors in Python using `psycopg2`  

All operations are implemented in the Jupyter notebook included in this project.

---

## Schema  

The database contains three tables:

**Product**  
- `prod_id`  
- `pname`  
- `price`  

**Depot**  
- `dep_id`  
- `addr`  
- `volume`  

**Stock**  
- `prod_id`  
- `dep_id`  
- `quantity`  

The Stock table links Product and Depot. Both foreign keys use cascading rules so that updates or deletions to parent rows are automatically propagated.

---

### Relationship Diagram  

```
Product (prod_id PK)        Depot (dep_id PK)
       |                          |
       |                          |
       +--------- Stock ----------+
                 (prod_id FK)
                 (dep_id FK)
```

## Tech Used  
- Python  
- PostgreSQL 15  
- psycopg2  
- pandas  
- matplotlib  
- tabulate  

---

## Running the Project  

### Install Dependencies  
```bash
pip install psycopg2 pandas tabulate matplotlib
```

### Update Database Credentials  
Inside the notebook, modify:

```python
DB_CONFIG = {
    "host": "localhost",
    "database": "postgres",
    "user": "your_username",
    "password": "your_password"
}
```

### Run the Notebook  
Execute all cells from top to bottom.

### Check Final Results  
Use the following query to inspect the final stock table:

```sql
SELECT * FROM stock;
```

---

## Why This Matters  
Working on this project helped me understand how real databases preserve integrity under different conditions. Instead of only reading about ACID properties, I could test them directly and observe how PostgreSQL manages cascading changes, rollbacks, isolation levels, and durability.

---

## About  
I completed this project for CS623 (Database Systems) as part of my Master’s in Data Science. It is designed to be a clear, practical illustration of transaction management using PostgreSQL and Python.
